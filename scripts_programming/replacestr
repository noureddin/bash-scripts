#!/bin/bash
function replacestr {
	#to replace the 'replace' command from mysql ;)
	#replace from to [from to] ... -- file1 [file2] ...
	#first: split input into two arrays: replacements and files
	rep=$(echo $@|sed 's/ -- .*//')
	rep=($rep)
	fil=$(echo $@|sed 's/.* -- //')
	#now we'll replace rep[0] with rep[1] in fil[0] and so on
	for ((i=0;i<${#fil[@]};i++))
	do
		file=${fil[$i]}
		index=`expr $i \* 2`
		rep1=${rep[$index]}
		rep2=${rep[`expr $index + 1`]}
		sed "s/$rep1/$rep2/" ${file} > ${file}.rep #replace the strings in the file
		mv ${file}.rep ${file} #we can't save to the same file, so we did this trick ;)
	done

}

replacestr $@