# linux-use-snippets (in no particular order)

These are snippets I have used as a computational biogist in my everyday work.

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
- ####  To check file permission and file list
```ls -lrt```
- #### To give right to the group to read and edit
``` chmod g+w ```
- #### Remove files with find – delete.
  First check which files to delete
``` find . -name "*.sam.gz" -type f ```
  Now delete
  ``` find . -name "*.sam.gz" -type f -delete```

- #### list file size in current dir
  ```du -sh -- * ```

- #### check file size of specific file
``` du -sh filename ```

- #### know free space
  ```df -h .```
- #### to include dotfiles
  ```du -sh -- * .*```
- #### total size of a current directory
  ```du -hs```
- #### Tar and compress multiple directories file by running
  ```tar -zcvf file.tar.gz dir1 dir2 dir3 ```
- #### Delete bams older than 90 days
  ```find . -name \*.bam -mtime +90 -print```
- #### find files with matching names and show their sizes
```
find . -name "*ReadsPerGene.out.tab" -exec ls -lh {} \; | awk '{print $5, $9}'
```
- #### delete all files in the current folder except for the files that match a specific pattern
```find . -maxdepth 1 ! -name "*QC.spliceJunctionAndExonCounts.forJunctionSeq.txt.gz" -type f -exec rm {} \;```

- #### delete all files in the current folder and its subdirectories, except for the files that match a specific pattern
```find . ! -name "*QC.spliceJunctionAndExonCounts.forJunctionSeq.txt.gz" -type f -exec rm {} +```
- #### list tar files 
```
tar -ztvf refdata-gex-mm10-2020-A.tar.gz
```
- #### open tar files
```
tar -xvf filename.tar.gz
```
- #### zip folders
```
zip -r <output_file> <folder_1> <folder_2> ... <folder_n>
zip -r temp.zip Documents
ls -l | grep .zip
```
- #### subset a gtf gene annotation file for a specific gene isoforms in linux
```
grep -w 'gene_identifier' input.gtf | awk '$3 == "transcript"'
```
