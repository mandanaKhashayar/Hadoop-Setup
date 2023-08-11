## Important note for windows users

If you are a windows user who wants to clone the code and then use it, remember that a typical configuration of **Git on windows** is to convert Unix-style \n-only line breaks to Windows-style \r\n line breaks on checking files out and re-converting to \n-only line breaks on committing. This would result in **env: bash\r: No such file or directory** after run the following scripts. So, to make Git check out files with Unix-style file endings on Windows - at least temporarily - use:
```
git config --global core.autocrlf false
```
Then run git clone URL. However to restore Git's behavior later, run 
```
git config --global core.autocrlf true
```

# Hadoop-Setup

Different configurations for setting up Hadoop (inside Vagrant)


**A_Standalone** A single node standalone setup which is a lite-version of Hadoop; you can run MapReduce jobs locally, but you do not connect to a HDFS filesystem or a Yarn resource manager. 
To setup, you need to manually run commands inside the VM:

```
cd /vagrant
./hadoop-download.sh
./hadoop-setup-standalone.sh
```

**B_Pseudo** Single node, running in Pseudo-distributed mode. In pseudo-distributed mode you set up HDFS and (eventually) YARN to work on a single computer. This is useful for testing purposes.
Commands:

```
cd /vagrant
./hadoop-download.sh
./ssh-setup.sh
./hadoop-setup-pseudo-distributed.sh
./hadoop-dfs-populate.sh
```

**C_Cluster** Three worker nodes and one master. In the fully distributed mode you extend the Pseudo-Distributed mode with more computers and setup HDFS and YARN so that they may work with all of these computers. Provisioned with the help of Puppet. Just `vagrant up` and everything should be fine.

**D_Docker_Cluster** Work in Progress, not ready yet.
