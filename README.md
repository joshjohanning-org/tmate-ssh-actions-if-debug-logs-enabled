# tmate-ssh-actions-if-debug

An example of doing something conditionally if it is a job with debug logging.

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
