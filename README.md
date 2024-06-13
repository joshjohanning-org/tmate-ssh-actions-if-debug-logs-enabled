# tmate-ssh-actions-if-debug-logs-enabled

An example of running a step conditionally if the job has debug logging enabled

The important bit is `$RUNNER_DEBUG` is set to 1 if is a debug job.

See:

```yml
      - name: create debug output
        id: debug
        run: |
          echo $RUNNER_DEBUG
          echo "RUNNER_DEBUG=$RUNNER_DEBUG" >> "$GITHUB_OUTPUT"

      - name: Setup tmate session
        if: steps.debug.outputs.RUNNER_DEBUG == 1
        uses: mxschmitt/action-tmate@v3
```
