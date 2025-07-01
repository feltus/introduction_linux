# introduction_linux

# lab-intro-to-linux-on-palmetto2

# Computational Lesson: Introduction to Linux and the Palmetto2 Cluster

# Overview
Linux is an operating system (OS) that allows software applications to run on computer hardware that consists of a motherboard, random access memory (RAM), central processing units (CPUs), graphics processing units (GPUs), disk storage, network interface cards (NICs), input devices (e.g. keyboard and mouse), and output devices (e.g. screens and printers). Click here for a great overview of [how a computer works](https://www.tutorialspoint.com/basics_of_computers/index.htm) and [how to build your own computer](https://www.pcmag.com/how-to/how-to-build-a-pc-the-ultimate-beginners-guide).

The most popular OS’s include macOS, Windows, Linux, and Android. All four have graphical user interfaces (GUIs) that allow users to open windows and click on graphical icons to interact with the computer. Another way to interact with a computer is with the command line interface (CLI) where commands are typed as text. The command line is a powerful environment to process a lot of data using text commands. Once you get the hang of it, you may find that GUIs sometimes get in the way when you are doing Digital Biology!

In this lab, you will remotely access the Palmetto2 computer cluster.  You will access Palmetto2 using the Open Ondemand software tool.

# Learning Objectives
* Access the Palmetto2 High Performance Computer (HPC) Cluster
* Navigate Linux file system on Palmetto2
* Download a genome sequence
* Compress/uncompress text files
* Interact with text files

# Part 1: Accessing the cluster.
* You have been granted a full feature educational account on the Palmetto2 cluster.
* To access the remote computer, open a web browser (Chrome, Safari, Edge, etc.) and go the the Clemson Ondemand site:  [Palmetto2](https://ondemand.rcd.clemson.edu)
* Start an interactive apps>>Jupyter Notebook session.  Change these resource allocations: CPU=4, memory=64GB, Number of Hours=12. This will create a 12 hour interactive session and allow you to interface with the cluster. When you launch new sessions, you can change the resource allocation if necessary.
* Once launched, open a terminal to interact with the cluster in the bash environment using a CLI.

# Part 2: Trying out basic linux commands.
Let’s download and uncompress the sea squirt (Ciona intestinalis) genome file. On the command line type:

```
wget http://hgdownload.soe.ucsc.edu/goldenPath/ci3/bigZips/ci3.fa.gz
```

Note: This command might be displayed on multiple lines but should be entered as one line.

See the name of the file with this command:

```
ls
```
Uncompress the file with this command:

```
gunzip ci3.fa.gz
# Note you can compress a file with the gzip command
```

See the new name of the file with this command:

```
ls
```

Type some Linux commands in the CLI.
NOTE: Linux is case sensitive so uppercase and lowercase letters are different.

# Display Linux system information:

```
uname
uname -a
```

NOTE: Linux commands often have arguments (e.g. -a) that allow you to modify the program behavior.

# List all files in a long listing (detailed) format:

```
ls
ls -a
ls -l
ls -al
man ls
```
NOTE: If you want to know more information about a command, type: man <command_name>

# Display the present working directory:
```
pwd
```
Note: A directory is just like a folder on your laptop.  It is a place to store files.

# Create a directory:
```
mkdir <diectory_name>
```

#Example: 
```
mkdir genomes
```
NOTE: The angled brackets represent text that the user types. In this case any directory name can be entered after the mkdir command. For example, you could make a ‘genomes’ directory.

# Copy files:
```
cp <fileA> <fileB>
#Example:
cp ci3.fa seasquirt.fa
```

# Rename or move files from one name or place to another. If fileB is an existing directory, move fileA into directory fileB:
```
mv <fileA> <fileB>
#Example: 
mv ci3.fa ciona_genome.fa
```

# Change directories:
```
cd <directory_name>
#Example: 
cd genomes
```

# View the contents of file:
```
cat <file_name>
# Browse through a text file:
less <file_name>

# Display the first 10 lines of file:
head <file_name>

# Display the last 10 lines of file:
tail <file_name>
```

```
# Remove (delete) file:
rm <file_name>
```
NOTE: Removing files in Linux can be dangerous. You will not be able to undo a delete! Be careful but don’t be afraid .

# Show free and used space on mounted filesystems:
```
df -h
```

# Display free and used RAM memory:
```
free -h
#( -h for human readable, -m for MB, -g for GB.)
```

# Display and manage the top running processes:
```
top
#Press q to quit top
```
NOTE: If you want to exit a program on the command line, press (CTRL + C) at the same time.

# Exit the terminal:

```
exit
```

# Part 3: Starting a new project on Palmetto.
# Create a working directory in scratch space on Palmetto.
Note:  When doing work on a shared cluster like Palmetto, always start by creating a working directory in the 'scratch space' and not your home directory.   Scratch space is a huge space to do work but it is temporary storage.  All files will be deleted in 30 days if they have not been accessed.  Scratch space is located in:

```
/scratch/<USERNAME>/ #Your Clemson User ID is your Linux account name (i.e. <USERNAME>)
```

```
#Example
cd /scratch/<USERNAME>
mkdir nematode_project_2025-12-13
```

Download and uncompress the nematode (Caenorhabditis elegans) genome assembly file in this working directory.  
```
wget https://ftp.ensembl.org/pub/release-114/fasta/caenorhabditis_elegans/dna/Caenorhabditis_elegans.WBcel235.dna.toplevel.fa.gz
gunzip Caenorhabditis_elegans.WBcel235.dna.toplevel.fa.gz
```

Examine the first 10 and last 10 lines on the uncompressed file;
```
head Caenorhabditis_elegans.WBcel235.dna.toplevel.fa
tail Caenorhabditis_elegans.WBcel235.dna.toplevel.fa
```

Redirect the output of headd to a plain text file with the '>' symbol.
```
head Caenorhabditis_elegans.WBcel235.dna.toplevel.fa > first10lines.txt
tail Caenorhabditis_elegans.WBcel235.dna.toplevel.fa > last10lines.txt
```

Combine the two files with 'cat'
```
cat first10lines.txt last10lines.txt > 20linesofDNA.txt
```

Here is a generative AI prompt to explain the concept of plain text files:

```
I'm starting computational biology work and need to understand text file basics better. Could you explain:
1. What makes a file "plain text" and why this format is essential for bioinformatics data
2. How to create and edit text files using command-line editors (nano, vim) in Linux environments
3. How to generate text files using bash redirection operators (>, >>, <<) with practical examples
4. Key differences in working with text files across Windows, macOS, and Linux platforms
5. Best practices for text file management in collaborative bioinformatics projects
Please include specific commands and examples relevant to genomic data workflows.
```

### **Useful Resources:**
- [ENSEMBL Database](https://www.ensembl.org/)
- [Palmetto2 User Guide](https://docs.rcd.clemson.edu/palmetto/)
