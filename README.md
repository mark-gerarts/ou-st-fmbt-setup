# fMBT configuration

## Usage

First follow [fMBT's install instructions](https://github.com/intel/fMBT). Then
you can run the following to view the model:

```markdown
fmbt-editor edit_value.aal edit_value.conf
```

## Offline test generation

To generate offline tests we adapted [fMBT's script](https://github.com/intel/fMBT/tree/master/examples/offline-test-suite)
to ignore inconcisiveness and just rely on random test generation.

Usage:

```markdown
./generate-all-tests enter_value.conf <number-of-tests>
```

This generates `<number-of-tests>` test files in the current directory. Because
the config has verbose logging, we can show exactly what a tester has to do:

```markdown
$ fmbt-log -f "\$tv\$ax\$aL" -S "\n----\n\n" test1.log | grep -v "AAL *"

focused = True
cellValue = ''
error = False
----

i:Add digit
----

focused = True
cellValue = '1'
error = False
----

i:Add digit
----

focused = True
cellValue = '16'
error = False
----

i:Leave focus

... and so on
```

So for this example the tester would:

- Add digit 1
- Add digit 6
- Leave focus
- ... and so on
