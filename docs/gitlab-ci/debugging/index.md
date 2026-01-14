# Mute Notifications While Debugging

Frequent commits or scheduled pipeline runs during troubleshooting can result in notification spam within the team Slack channel. To address this, we utilize a branch-based filtering strategy.

The UAB RC Slack integration is configured to send notifications **only for pipelines running on the default branch**. By running your pipeline on a non-default branch, you can execute as many test runs as needed without triggering Slack alerts.

## How to Mute Notifications

1. **Create and Push a Temporary Branch**
   Create a branch from your current development head using a descriptive name (e.g., `temp-debug-pipeline`).
1. **Run and Monitor the Pipeline**
   After pushing the branch, you may need to trigger the pipeline manually depending on the project's CI configuration. Since this is a non-default branch, Slack notifications will remain muted.
1. **Cleanup After Success**
   After you have confirmed your fix and the pipeline is successful, merge your changes into your primary development branch and remove the temporary branch to keep the repository clean.

## Enable CI_DEBUG_TRACE

### Enabling debug mode for GitLab CI pipelines

GitLab provides a predefined CI/CD variable, CI_DEBUG_TRACE, that enables verbose debug output for job execution. This is useful when you need to see the variable interpolation in the job

When set to "true", the job log shows every command as it executes and prints the environment variables available to the job, which helps with troubleshooting variable expansion and script behavior.

### Enabling debug for a single job in .gitlab-ci.yml

To turn on debug mode for a specific job, define CI_DEBUG_TRACE under that job's variables section:

```yaml
debug_example_job:
  stage: test
  variables:
    CI_DEBUG_TRACE: "true"
  script:
    - echo "Debug trace is enabled for this job"
    - ./run-tests.sh
```

!!! note

    - Debug trace applies only to `debug_example_job`; other jobs in the pipeline run with normal logging.
    - To turn debug off for this job, either remove `CI_DEBUG_TRACE` or set it to `"false"` and re-run the pipeline.

### Enable debug for the whole pipeline

Enable debug mode for the entire pipeline by manually setting the `CI_DEBUG_TRACE` variable:

1. In your project, navigate to **Build > Pipelines**.
1. Click the **Run pipeline** button.
1. In the **Variables** section of the form, add a new variable:
    - **Key:** `CI_DEBUG_TRACE`
    - **Value:** `true`
1. Click **Run pipeline**.

All jobs within that specific pipeline run will detect `CI_DEBUG_TRACE` and emit verbose debug trace information in their respective logs.
