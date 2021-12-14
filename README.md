# linux-use-snippets

- #### remove all files starting with a certain string in Linux
`find  . -name 'name*' -exec rm {} \;`

- #### Count Files in Directory
`ls -l | wc -l`

- #### Convert fasta sequence to uppercase
`awk '/^>/ {print($0)}; /^[^>]/ {print(toupper($0))}' file.fasta > file_upper.fasta`
src: https://gist.github.com/l-modolo/3384b250006b59e54157

- #### Find read length in fastq
`cat input.fq | awk '{if(NR%4==2) print length($1)}' > input.readslength.txt`
`zcat input.fastq.gz | awk '{if(NR%4==2) print length($1)}' | uniq -c`

- #### gzip all files
```
for f in *.gz; do
    echo $f
    gzip -t $f
done
```

