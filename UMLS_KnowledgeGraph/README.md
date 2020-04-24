# UMLS Knowledge Sources Tutorial
This is instruction on how to make use of UMLS to generate the knowledge graph dataset. 


The Three UMLS Knowledge Sources
[Metathesaurus](https://www.nlm.nih.gov/research/umls/knowledge_sources/metathesaurus/index.html): Terms and codes from many vocabularies, including CPT, ICD-10-CM, LOINC, MeSH, RxNorm, and SNOMED CT. Hierarchies, definitions, and other relationships and attributes.
[Semantic Network](https://semanticnetwork.nlm.nih.gov/): Broad categories (semantic types) and their relationships (semantic relations).
[SPECIALIST Lexicon and Lexical Tools](https://lexsrv3.nlm.nih.gov/Specialist/Home/index.html): A large syntactic lexicon of biomedical and general English and tools for normalizing strings, generating lexical variants, and creating indexes.


## Install:

[Install software guide](https://www.nlm.nih.gov/research/umls/implementation_resources/metamorphosys/help.html)

## Dataset:

[data set description](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.4)
Some examples:


[Concepts Names and Sources](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.4)\

[Semantic Network](https://www.ncbi.nlm.nih.gov/books/NBK9679/)
      [Basic information about the Semantic Types and Relations.] : 
       
       SRDEF:
            SRDEF:Basic information about the Semantic Types and Relations.

              Field	Description
              RT:	Record Type (STY = Semantic Type or RL = Relation).
              UI:	Unique Identifier of the Semantic Type or Relation.
              STY/RL:	Name of the Semantic Type or Relation.
              STN/RTN:	Tree Number of the Semantic Type or Relation.
              DEF:	Definition of the Semantic Type or Relation.
              EX:	Examples of Metathesaurus concepts with this Semantic Type (STY records only).
              UN:	Usage note for Semantic Type assignment (STY records only).
              NH:	The Semantic Type and its descendants allow the non-human flag (STY records only).
              ABR:	Abbreviation of the Relation Name or Semantic Type.
              RIN:	Inverse of the Relation (RL records only).
 
       SRSTR: Structure of the Network.
            Field	Description
            STY/RL:	Argument 1 (Name of a Semantic Type or Relation).
            RL:	Relation ("isa" or the name of a non-hierarchical Relation).
            STY/RL:	Argument 2 (Name of a Semantic Type or Relation); if this field is blank this means that the Semantic     Type or Relation is one of the top nodes of the Network.
            LS:	Link Status (D = Defined for the Arguments and its children; B = Blocked; DNI = Defined but Not Inherited by the children of the Arguments).
            N.B.: The relations expressed in this table are binary relations and the arguments are ordered pairs. The relations are stated only for the top-most node of the "isa" hierarchy of the Semantic Types to which they may apply.
[Semantic Types](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.7)
  
[Semantic Relationship ](https://www.ncbi.nlm.nih.gov/books/NBK9685/#ch03.sec3.3.4)



```
#!/bin/sh

#SBATCH --job-name= your_job_name

#SBATCH --account=vgvinodv
#SBATCH --partition=gpu 

#SBATCH --mail-user=youremail@umich.edu
#SBATCH --mail-type=BEGIN,END

#SBATCH --nodes=1
#SBATCH --gres=gpu:1
#SBATCH --mem=20G
#SBATCH --time=10:00:00

source ./your_env_name/bin/activate

python  your_code1.py
python  your_code2.py
python  your_code3.py
```

Some instructions:
1. `#SBATCH --job-name= your_job_name` Give a name of your job.
2. `#SBATCH --partition=gpu ` For partitions, you can choose gpu,standard,viz,largemem for different useage.
3. `#SBATCH --mail-user=youremail@umich.edu` Set one email address to get notification of your job status.
  or you can use `squeue -u uniquename` to list all your jobs.
4. `#SBATCH --nodes=1`  Choose number of nodes you want.
5. `#SBATCH --gres=gpu:1` number of Gpu for this node, remember to remove this command when you use CPU only
6. `#SBATCH --time=10:00:00` max time you want to use this node, job will be ended anyway even if job hasn't been finished.

7. `source ./your_env_name/bin/activate` You need to activate your virtual environment to settle the env you want. You need to adjust the path based on your folder structure. 
For this bashfile, they are all in same level.
```
-your_env_folder
-your_code.py
-bashfile.sh
-xxxxx.out
```
8. You can see the log information or error traceback helping debug in jobnumber.out under the same folder of your bashfile.


## Actions command:

`sbatch xxx.sh` submit your bashfile

`squeue -u uniquemane` check your jobs status

`scancel jobid` delete your job, you will get one jobid after you submit.

More in Cheat sheet

## Document Management GUI on Mac

I recommand `Cyberduck` for document management uploading, downloading,etc.

When setting connections, use `FTP` protocal , server name `greatlakes.arc-ts.umich.edu` , `your unique name` and `password`.
