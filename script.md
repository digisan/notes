## find Linux binary files
> `find . -type f -executable -exec sh -c "file -i '{}' | grep -q 'x-executable; charset=binary'" \; -print`

## delete Linux binary files
> `find . -type f -executable -exec sh -c "file -i '{}' | grep -q 'x-executable; charset=binary'" \; -print | xargs rm -f`

## find Mac binary files
> `find . -type f -executable -exec sh -c "file -i '{}' | grep -q 'x-mach-binary; charset=binary'" \; -print`

## delete Mac binary files
> `find . -type f -executable -exec sh -c "file -i '{}' | grep -q 'x-mach-binary; charset=binary'" \; -print | xargs rm -f`

## find windows executables
> `find . -type f -executable -exec sh -c "file -i '{}' | grep -q 'x-dosexec; charset=binary'" \; -print`

## delete windows executables
> `find . -type f -executable -exec sh -c "file -i '{}' | grep -q 'x-dosexec; charset=binary'" \; -print | xargs rm -f`

## delete others
> `for f in $(find ./ -name '*.log' -or -name '*.doc'); do rm $f; done`

## find some* process port
> `sudo lsof -i -P -n | grep some`