===============================================================
SOP - managing replacement of experiments and experiment sets
===============================================================

On occasion a lab decides to change the raw files or experiments associated with released data sets.  While this practice is discouraged there are cases where we need to accommodate these changes.  This document describes scenarios and associated actions to perform.
When to replace an experiment / experiment set.

.. note:: The raw files referred to by a **released** experiment or experiment set should be persistent.

.. note:: **released** and **released to project** are treated equivalently and **released** will be used to mean either during the remainder of this document.

Scenario I - New Replicate Experiments
========================================

A lab produces additional replicates to add to a *released* replicate set.

#. Create a new ExperimentSetReplicate Item
#. Create the new replicate Experiment(s) Item
#. Link all the Experiments to the newly created ExperimentSetReplicate (newly created in step 2
   and existing ones of the set to be replaced)
#. If processed_files exist on the old set

  * move to other_processed_files on the old set
  * with a clear title and description as to why they were moved
  * other_processed_files.type == archived
  * set status of files to archived {to project}
#. if other_processed_files exist on the old sets
    * change other_processed_files.type == archived
    * set status of files to archived {to project}

, and add the old one as alternate_accession
On omics call (Feb 25th 2019) we discussed if small differences between "replicates" are tolerable. The conclusion was to handle it case by case, and in every case make sure that the differences made visible with a badge and a message and also with descriptions.  ?
If a lab wants to modify the  raw files on a released/to project experiment (see adding raw/processed files)
See the data freeze policy here: https://docs.google.com/document/d/1Bub75UVnT3mIXpXStOH8w2mW3-HjLIhQpLvmke8UAQI/edit

Anytime you replace an item (with accession)
IMPORTANT! Before you start, make sure that new item is ready to carry the status of the old one. If you are about to replace a new set, replacing a released one, the new one should switch to released after replacement, otherwise we can run into access problems

Only replace experiments or experimentSets. Files only get archived.
To replace, Change the status of the old item to "replaced", and modify the new one by  adding the accession of the replaced item as an "alternate_accessions" to the new item. Match the status of the new item to the status from the previous one.
Create two new static sections that describe why the replacement took place, linking in both directions.
e.g. 4DNESXDO3862 and 4DNESC5FAH5U.
For this process, we have a notebook in dcicwranging repo, useful_notebooks/190128 Replacing experiment sets.ipynb that takes care of replacement and static sections.


Adding a new replicate experiment (replacing experiment sets)
This is the most common case we had so far, when labs want to add more experiments (biological or technical replicates) to an existing set
Prepare your new experiments.
Create a new set, and add all the experiments that are associated with it (the new experiments you prepared, and the experiments from the old set.
If there are processed files on the old set, keep them as part of the old set, but move them to other_processed_files, with a clear reason and title, and change status to archived/ to project
If there are other_processed_files on the old set, change their status to archived/ to project
Go through the replacement protocol, and make sure the status are matching.
Note: If the lab wants to add more experiments, but wants to keep the new set at a lower status than the previous set, it won't be allowed. In this case, you can prepare the new set, but don't go through the replacement and release, until they are ready to match the status.a


Adding new files (replacing experiments)

New files always need to be created from scratch. If there are wrong files, delete them when they are not released, and archive them when they are released.

Adding a new raw file (e.g. sequencing replicate)
If set/exp is not released yet, you can add the new files to the existing experiment, and delete the wrong files. No need for replacement. The steps below are for released/to project items.

Prepare your new experiment with all the files it needs (new ones and if any files needed from the old experiment)
If there are processed files on the old exp, add them to other_processed_files, with a clear reason and title, and change status to archived/ to project.
If there are other_processed_files on the old exp, change their status to archived/ to project.
For released/to project raw files that are no longer needed from the old experiment, archive/to project them and add to other_processed_files with title "Archived raw files", and description explaining the reason.
Replace the old experiment with the new one following instructions above.
Follow steps on "adding a new replicate experiment"
Adding new processed files
If there are replaced sets and experiments:

If there are processed files on the old exp, add them to other_processed_files, with a clear reason and title, and change status to archived/ to project
If there are other_processed_files on the old exp, change their status to archived/ to project
Outcome
The replaced items will be hidden on the browse/search page by default.
The resulting change is reported well on the next data release updates.
Replaced items have an automated redirect setup, e.g.
this redirects to the new item: https://data.4dnucleome.org/experiment-set-replicates/4DNESXDO3862
the old item can be accessed via the uuid: https://data.4dnucleome.org/experiment-set-replicates/f76f9174-1b6a-4261-9e55-c004397d218a/


Unsolved Cases:

When 'released to project' status items are replaced, they became available to public.
Not pretty but not a huge issue, since files are archived to project, processed_files are moved to opf. All they see is an empty expset if they can find their way there.
