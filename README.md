# SACLA2016B8055
Data analysis repository for SACLA experiment between October 27-31, 2016 (proposal number: 2016B8055)

--------------------------------------------------------------------------------

DataConvert
-----------

- VPN into your SACLA account using CISCO:

  `hpc.spring8.or.jp`

- Login to one of the analysis nodes at SACLA:

  `ssh -X fperakis@xhpcfep`

  `qsub -I -X`

- Run `MakeTagList` to extract tag numbers from data:

  `MakeTagList -b 3 -r 219560 -inp condition0001.txt -out tag_number0001.list`

- Run `DataConvert4` to extract the data to HDF5 format:

  `DataConvert4 -f test0001.conf -l tag_number0001.list -dir ./ -o test0001.h5`

- Alternatively, run `DataConverterGUI`:

  `DataConverterGUI`

- Run `dataCompress3.py` using Python 2.7 to produce averages for each scan position (OBS: uses DataConvert3):

  `python2.7 dataCompress3.py -f 259782.h5 -c run259782_out.csv -a`

Submit
------

- VPN into your SACLA account using CISCO:

  `hpc.spring8.or.jp`

- Login to one of the analysis nodes at SACLA:

  `ssh -X fperakis@xhpcfep`

- Go to the active UserData folder with the source code:
  
  `cd /UserData/fperakis/2016_10/codes`

- Pre-process darks using `qsub`:

  `./pre_process_dark.sh 498492`

- Pre-process BG-subtracted runs using `qsub`:

  `./pre_process_run.sh 498491 498492`

- Pre-process several runs/darks by appending more runs than 2/1, run the scripts without arguments for help.

Information
-----------

- Check run status in experiment spreadsheet on [Google Drive](https://docs.google.com/spreadsheets/d/1tc8wDE6LAOmk0neN5kzumP-UFSdcJCignMXozlqEuTU/)

  `Data` sheet shows login information

  `Runs` sheet shows run information

- Check experiment run log on [Google Drive](https://docs.google.com/document/d/1MFH32yqhbSEncKCUKT8HPQzEcjCuRDoLvFBTThcdYhM/)

- Check data analysis information at [HPC](http://xhpcfep.hpc.spring8.or.jp/manuals/)
