The `--duration=10` option in the `arecord` command specifies that the recording will last for 10 seconds. This is how long the microphone will record before stopping and saving the output to the `test.wav` file.

**For example:**
If you want the recording to last 120 seconds, you would specify `--duration=120`
```shell
arecord --duration=120 test.wav
```
