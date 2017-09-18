# singularity
How to use Singularity containers for running single cell batch effect correction algorithms

## Installing Singularity on your university's high performance computing (HPC) cluster

### Documentation for your Cluster Administrators
Many cluster administrators are wary of Singularity because of security issues and since they have to stinall it as `root`. If this is the case, we have some resources for you!

Your cluster administrators should read this :
-	"Singularity Administration Guide" at http://singularity.lbl.gov/admin-guide

If they have security questions, there is a detailed documentation about security here:
-	http://singularity.lbl.gov/docs-security

The Singularity team is very responsive and happy to help with any questions in these forums:
- https://groups.google.com/a/lbl.gov/forum/#!forum/singularity
- https://singularity-container.slack.com/
- https://stackoverflow.com/search?q=singularity

Also please message Alain on slack or email, and he'll try to help.

## Using Singularity

How to test your singularity installation with a small, simple container:
```
singularity run shub://vsoch/hello-world
```
The output should be “Hello”
Procedure:

```
mkdir scbatch
cd scbatch
# the next line downloads a big file and will take a few minutes

singularity run shub://2377
source .scbatchrc

# Launch a Jupyter Notebook with all of the algorithms loaded
scbatch_notebook
```


## Troubleshooting/debugging

### To help troubleshoot if you have singularity installation issues

It would be helpful if you could run these commands in this specific order and provide me with the outputs you get:
```
pwd
df -h
module load singularity
singularity --version
which singularity
ls -l $(which singularity)
grep "bind path =" $(dirname $(which singularity))/../etc/singularity/singularity.conf 
```

Common pitfalls:
- wrong version of singularity (step 4 should give you 2.3.1)
- Singularity not installed as root  (step 6 should show that singularity command is owned by root)
- storage drives not included in the singularity.conf configuration file (step 7 should include all drives seen in step 5 that you are going to use)



### Notes about cluster drives for different locations

#### SDSC TSCC - Alain Domissy
```
bind path = /oasis
bind path = /projects
```

#### West Virginia University - Ashley Brandebura
```
bind path = /users
bind path = /gpfs
bind path = /group
```

#### Cincinnati Children's Hospital
```
bind path = /users
bind path = /data
bind path = /scratch
```

