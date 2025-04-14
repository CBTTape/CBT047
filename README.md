# CBT047
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 047 IS FROM TORONTO HYDRO IN TORONTO, ONTARIO, CANADA.    *   FILE 047
//*           THIS FILE CONTAINS THE FOLLOWING, FOR ADDITIONAL      *   FILE 047
//*           INFORMATION SEE THE MEMBER CALLED $INDEX : (THIS      *   FILE 047
//*           FILE ALSO USES SOME MACROS THAT ARE IN FILES 435 AND  *   FILE 047
//*           OR 464. THIS FILE HAS BEEN SUBMITTED BY MR JIM LANE   *   FILE 047
//*                                                                 *   FILE 047
//*           THE CURRENT FILE IS A REFRESH AS OF 12/09/93.         *   FILE 047
//*                                                                 *   FILE 047
//*           Some pieces from the 06/04/89 version of this file    *   FILE 047
//*           have been grafted back in.  For example, JCLFLOW,     *   FILE 047
//*           the EXITS member, and Jim's older SAS programs.       *   FILE 047
//*           The ISPF stats will tell you which member is newer,   *   FILE 047
//*           and which is older.                                   *   FILE 047
//*           (Sam Golob - 08/08/01 - taken from CBT352)            *   FILE 047
//*                                                                 *   FILE 047
//*           THIS FILE ALSO CONTAINS AN ESA VERSION OF CMD1.       *   FILE 047
//*           (SEE THE BF GOODRICH VERSION ON FILE 261 WHICH MAY    *   FILE 047
//*           BE FOR A HIGHER LEVEL OF MVS/ESA.)                    *   FILE 047
//*                                                                 *   FILE 047
//*           JIM'S CURRENT ADDRESS:                                *   FILE 047
//*                                                                 *   FILE 047
//*                JIM LANE                                         *   FILE 047
//*                TORONTO HYDRO                                    *   FILE 047
//*                TECHNICAL SERVICES                               *   FILE 047
//*                14 CARLTON STREET                                *   FILE 047
//*                TORONTO, ONTARIO  M5B 1K5                        *   FILE 047
//*                CANADA                                           *   FILE 047
//*                416-542-2820   direct line                       *   FILE 047
//*                                                                 *   FILE 047
//*   Note:  Jim Lane is now doing AIX, and this file is            *   FILE 047
//*          now "functionally stabilized" until somebody           *   FILE 047
//*          else takes it over.    (SG - 07/99)                    *   FILE 047
//*                                                                 *   FILE 047
//*            THIS PDS CONTAINS THE FOLLOWING MEMBERS:             *   FILE 047
//*                                                                 *   FILE 047
//*           EDX      - "PERSONAL DATASET MANAGER" ISPF DIALOG.    *   FILE 047
//*           EXITS    - SOME JES2 AND MPF EXITS.                   *   FILE 047
//*           JCLFLOW  - AN ISPF PROGRAM EDIT MACRO TO NEATLY       *   FILE 047
//*                      FORMAT JCL                                 *   FILE 047
//*           LISTICAT - A BATCH PROGRAM TO 1-UP LIST DATASETS IN   *   FILE 047
//*                      AN ICF CATALOG.                            *   FILE 047
//*           NOCELL   - A BATCH PROGRAM TO LIST DISK, TAPE AND     *   FILE 047
//*                      HSM MIGRATED DATASETS                      *   FILE 047
//*           RMFIII   - A POST PROCEESOR FOR RMF MONITOR III       *   FILE 047
//*                      DATA.                                      *   FILE 047
//*           SASEREP  - A SAS PROGRAM TO PROCESS LOGREC RECORDS.   *   FILE 047
//*           SASGTF   - A SAS PROGRAM TO PROCESS GTF SVC TRACE     *   FILE 047
//*                      RECORDS.                                   *   FILE 047
//*           SASHSM   - A SET OF SAS PROGRAM TO ANALYZE HSM USAGE  *   FILE 047
//*           SASRMF79 - A SAS PROGRAM TO PROCESS RMF TYPE 79       *   FILE 047
//*                      RECORDS.                                   *   FILE 047
//*           SASSYSLG - A SAS PROGRAM TO PROCESS SYSLOG DATA.      *   FILE 047
//*           SASTLMS  - A SAS PROGRAM TO PROCESS THE TLMS II       *   FILE 047
//*                      VOLUME MASTER FILE.                        *   FILE 047
//*           SMPELIST - A BATCH PROGRAM TO 1-UP LIST ENTRIES FROM  *   FILE 047
//*                      AN SMP-E CSI.                              *   FILE 047
//*                                            - EDX -              *   FILE 047
//*              AN ISPF DIALOG CALLED "PERSONAL DATASET MANAGER".  *   FILE 047
//*              EDX MAINTAINS AND DISPLAYS A TABLE OF DATASET      *   FILE 047
//*              NAMES (OPTIONALLY INCLUDING A MEMBER NAME). THE    *   FILE 047
//*              FOLLOWING OPERATIONS CAN BE REQUESTED ON ANY OF    *   FILE 047
//*              THE DATASETS:                                      *   FILE 047
//*             ?         TO DISPLAY INFORMATION ABOUT THE          *   FILE 047
//*                       DATASET'S ATTRIBUTES.                     *   FILE 047
//*             A         TO ALLOCATE A NEW DATASET USING THIS ONE  *   FILE 047
//*                       AS A MODEL.                               *   FILE 047
//*             B         TO ISPF BROWSE THE DATASET.               *   FILE 047
//*             D         TO DELETE THE DATASET.                    *   FILE 047
//*             E         TO ISPF EDIT THE DATASET.                 *   FILE 047
//*             HM        TO MIGRATE THE DATASET WITH DFHSM.        *   FILE 047
//*             HR        TO RECALL THE DATASET FROM DFHSM          *   FILE 047
//*                       MIGRATION.                                *   FILE 047
//*             P         TO INVOKE THE PDS84 DIALOG ON THE         *   FILE 047
//*                       DATASET.                                  *   FILE 047
//*             PR        TO PRINT THE DATASET.                     *   FILE 047
//*             V         TO SET OR UPDATE THE VOLSER FIELD.        *   FILE 047
//*             X         TO DROP THE DATASET FROM THE LIST.        *   FILE 047
//*                                                                 *   FILE 047
//*              EDX PICKS UP ON THE FACT THAT A DATASET HAS BEEN   *   FILE 047
//*              MIGRATED AND DISPLAYS A MESSAGE TO THAT EFFECT IF  *   FILE 047
//*              YOU TRY TO DO SOMETHING THAT NEEDS THE DATASET     *   FILE 047
//*              UNMIGRATED. YOU HAVE TO EXPLICITLY HRECALL IT      *   FILE 047
//*              FIRST.                                             *   FILE 047
//*                                                                 *   FILE 047
//*              THIS DATASET ALSO CONTAINS UPDATED VERSIONS OF     *   FILE 047
//*              THE ED AND BR COMMAND TABLE COMMANDS THAT ADD THE  *   FILE 047
//*              DATASET YOU EDIT OR BROWSE TO THE EDX DATASET      *   FILE 047
//*              TABLE. THEY ALSO ACCEPT AN OPERAND OF "*" TO MEAN  *   FILE 047
//*              THE MOST RECENT DATASET YOU EITHER EDITED OR       *   FILE 047
//*              BROWSED.                                           *   FILE 047
//*                                           - EXITS -             *   FILE 047
//*              A SET OF JES2 AND MPF EXITS:                       *   FILE 047
//*                EXIT02   - ENFORCE JOBNAME AND JOBCLASS          *   FILE 047
//*                           STANDARDS                             *   FILE 047
//*                EXIT03   - CANCEL JOBS FLAGGED BY EXIT02         *   FILE 047
//*                EXIT04   - DUMMY OUT JOBCAT AND STEPCAT DD       *   FILE 047
//*                           STATEMENTS                            *   FILE 047
//*                MPFABEND - HIGHLIGHTED WTO FOR ABENDING          *   FILE 047
//*                           PRODUCTION JOB                        *   FILE 047
//*                MPFHOLD  - REPLY NOHOLD TO IEF433D               *   FILE 047
//*                MPFJCLER - HIGHLIGHTED WTO FOR PRODUCTION JOB    *   FILE 047
//*                           WITH JCL ERROR                        *   FILE 047
//*                MPFVINIT - START TSO AFTER VTAM IS UP            *   FILE 047
//*                MPFVTAM  - HIGHLIGHTED WTO WHEN NETWORK NODES    *   FILE 047
//*                           GO INACT                              *   FILE 047
//*                                            - JCLFLOW -          *   FILE 047
//*              THIS PROGRAM WAS "OBTAINED" FROM FILE352 OF THE    *   FILE 047
//*              CBT TAPE. IN ITS ORIGINAL FORM IT WAS A BATCH      *   FILE 047
//*              UTILITY, READING JCL FROM SYSUT1 AND WRITING THE   *   FILE 047
//*              REFORMATTED STUFF ONTO SYSUT2. I CHANGED IT BY     *   FILE 047
//*              ALTERING THE I/O LOGIC TO USE ISPF EDIT MACRO      *   FILE 047
//*              SERVICES. THE BASIC LOGIC IS TO START AT THE TOP   *   FILE 047
//*              OF THE DECK ASSIGNING EACH LINE TO VARIABLE        *   FILE 047
//*              "CARD". ANYTHING OTHER THAN PART OF A DD           *   FILE 047
//*              STATEMENT IS LEFT AS IS. WHEN A DD STATEMENT IS    *   FILE 047
//*              FOUND EACH LINE IS DELETED AFTER BEING READ. THE   *   FILE 047
//*              LINE NUMBER AFTER WHICH TO INSERT REFORMATTED JCL  *   FILE 047
//*              IS REMEMBERED IN VARIABLE "ADDLINE". AN ENTIRE DD  *   FILE 047
//*              STATEMENT IS READ IN, CONTINUATION LINES AND ALL   *   FILE 047
//*              AND STORED IN "TABLEIN", EACH INPUT LINE BEING     *   FILE 047
//*              DELETED AFTER ASSIGNMENT. THE DD STATEMENT IS      *   FILE 047
//*              THEN FORMATTED BY BEING COPIED ONE PARAMETER AT A  *   FILE 047
//*              TIME OVER TO "TABLEOUT". FROM "TABLEOUT" NEW       *   FILE 047
//*              LINES ARE INSERTED INTO THE DATASET TO CONTAIN     *   FILE 047
//*              THE REFORMATTED DD STATEMENT. SINCE THE NUMBER OF  *   FILE 047
//*              LINES IN THE DATASET COULD HAVE INCREASED, THE     *   FILE 047
//*              LINE NUMBER OF THE LAST LINE IS RE-CALCULATED AS   *   FILE 047
//*              NECESSARY AND REMEMBERED IN VARIABLE "LLINE".      *   FILE 047
//*                                            - LISTICAT -         *   FILE 047
//*            NAME         LISTICAT                                *   FILE 047
//*            FUNCTION     LIST THE CONTENTS OF AN ICF CATALOG     *   FILE 047
//*                         AND SELECTED DSCB AND VVDS FIELDS.      *   FILE 047
//*            DESCRIPTION  THE UCBS OF ALL ONLINE DASD VOLUMES     *   FILE 047
//*                         ARE LOCATED AND AN ATTEMPT IS MADE TO   *   FILE 047
//*                         ALLOCATE SYS1.VVDS.VVOLSER.  IF THIS    *   FILE 047
//*                         WORKS AN ACB AND RPL ARE GENERATED AND  *   FILE 047
//*                         THEIR ADDRESSES ARE SAVED IN A LOOKUP   *   FILE 047
//*                         TABLE.  THE BCS CLUSTER IS OPENED AS A  *   FILE 047
//*                         DATASET AND READ SEQUENTIALLY. THE BCS  *   FILE 047
//*                         RECORDS ARE SCANNED FOR CELL TYPES AND  *   FILE 047
//*                         THE FOLLOWING CELLS ARE LISTED:         *   FILE 047
//*                           NONVSAM                               *   FILE 047
//*                           CLUSTER                               *   FILE 047
//*                           INDEX                                 *   FILE 047
//*                           DATA                                  *   FILE 047
//*                           AIX                                   *   FILE 047
//*                           PATH                                  *   FILE 047
//*                           GDG BASE                              *   FILE 047
//*                           GDG ENTRY                             *   FILE 047
//*                         FOR NONVSAM ENTRIES THE FORMAT1 AND,    *   FILE 047
//*                         IF IT EXISTS THE FORMAT 3, DSCB IS      *   FILE 047
//*                         "OBTAINED" TO DETERMINE IF THE OBJECT   *   FILE 047
//*                         EXISTS. IF IT DOES THE LRECL, BLKSIZE   *   FILE 047
//*                         AND TOTAL TRACKS ALLOCATED ARE          *   FILE 047
//*                         EXTRACTED.  IF THE OBJECT IS            *   FILE 047
//*                         CATALOGED TO VOLSER "MIGRAT" THE        *   FILE 047
//*                         DFHSM MIGRATION CONTROL DATASET IS      *   FILE 047
//*                         OPENED (SYSUT2) AND USED INSTEAD OF     *   FILE 047
//*                         THE VTOC.                               *   FILE 047
//*                                                                 *   FILE 047
//*                         FOR DATA AND INDEX ENTRIES THE VVDS OF  *   FILE 047
//*                         THE VOLUME IN QUESTION, IF AVAILABLE,   *   FILE 047
//*                         IS SCANNED TO DETERMINE THE LRECL,      *   FILE 047
//*                         BLKSIZE AND TRACK ALLOCATION OF THE     *   FILE 047
//*                         OBJECT.                                 *   FILE 047
//*                                                                 *   FILE 047
//*            ENVIRONMENT  OS/VS2 MVS, JDM1113 OR HDQ1102          *   FILE 047
//*                         MVS/XA 2.1.7 DF/HSM 2.1.0               *   FILE 047
//*                         (HAS BEEN RUN ON MVS/ESA.)              *   FILE 047
//*            INPUT        THE BCS OF THE ICF CATALOG TO BE        *   FILE 047
//*                         LISTED.                                 *   FILE 047
//*            OUTPUT       OUTPUT CONSISTS OF A LISTING OF THE     *   FILE 047
//*                         CATALOG.                                *   FILE 047
//*                                             - NOCELL -          *   FILE 047
//*            NAME         NOCELL                                  *   FILE 047
//*             INTRODUCTION                                        *   FILE 047
//*             NOCELL IS A UTILITY THE PURPOSE OF WHICH IS TO      *   FILE 047
//*             ANALYZE ALLOCATED DATASETS.  THE  PROGRAM  CAN      *   FILE 047
//*             PROCESS ALL DATASETS OR SELECT A SUBSET, AND        *   FILE 047
//*             PRODUCE DETAIL LISTINGS OR SUMMARY REPORTS.         *   FILE 047
//*             JCL REQUIREMENTS.                                   *   FILE 047
//*             NOCELL CAN BE EXECUTED USING THE FOLLOWING JCL:     *   FILE 047
//*               //STEP     EXEC PGM=NOCELL,REGION=4096K           *   FILE 047
//*               //STEPLIB  DD DSN=<YOUR.LOADLIB>,DISP=SHR         *   FILE 047
//*               //SYSUT1   DD DSN=<HSM.MCDS>,DISP=SHR             *   FILE 047
//*               //SYSUT2   DD DSN=<HSM.BCDS>,DISP=SHR             *   FILE 047
//*               //VMF      DD DSN=<TLMSII.VMF>,DISP=SHR           *   FILE 047
//*               //CATALOG  DD DSN=<ASM2.ARCHIVE.CATALOG>,DISP=SHR *   FILE 047
//*               //SYSUDUMP DD SYSOUT=                             *   FILE 047
//*               //SYSIN    DD                                     *   FILE 047
//*               /*                                                *   FILE 047
//*            INSTALLATION  JCL TO INSTALL NOCELL IS CONTAINED IN  *   FILE 047
//*                          MEMBER $INSTALL WHICH ASSEMBLES AND    *   FILE 047
//*                          LINKS THE CODE AND COPIES THE          *   FILE 047
//*                          ELEMENTS OF THE ISPF DIALOG TO THE     *   FILE 047
//*                          PROPER LIBRARIES                       *   FILE 047
//*            DOCUMENTATION A USER'S GUIDE COMPLETE WITH JCL       *   FILE 047
//*                          EXAMPLES IS IN MEMBER $DOC. YOU WILL   *   FILE 047
//*                          NEED IBM'S DCF TO PRINT THIS MEMBER.   *   FILE 047
//*                                             - RMFIII -          *   FILE 047
//*             NAME         ERB3POST                               *   FILE 047
//*             FUNCTION     READS THE DATASET PRODUCED BY RMF 3.4  *   FILE 047
//*                          MONITOR III, WRITES A REPORT OF        *   FILE 047
//*                          POSSIBLE ANOMALIES AND WRITES TWO      *   FILE 047
//*                          SEQUENTIAL FILES (ONE ABOUT ADDRESS    *   FILE 047
//*                          SPACES AND ONE ABOUT DEVICES)          *   FILE 047
//*                          SUMMARIZING THE MONITOR III            *   FILE 047
//*                          MEASUREMENTS.                          *   FILE 047
//*             DESCRIPTION  THE DATASET PRODUCED BY RMF MONITOR    *   FILE 047
//*                          III AS OF 3.4 IS NOT IN ANY WAY        *   FILE 047
//*                          NORMAL. IT IS A VSAM ESDS OF 32K       *   FILE 047
//*                          RECORDS. THE 1ST RECORD, AFTER SOME    *   FILE 047
//*                          DESCRIPTIVE DATA IS FILLED WITH AN     *   FILE 047
//*                          ARRAY OF 28 BYTE POINTERS DESCRIBING   *   FILE 047
//*                          "SETS OF SAMPLES". A SET OF SAMPLES    *   FILE 047
//*                          IS WHAT MONITOR III CALCULATES EVERY   *   FILE 047
//*                          "MINTIME" SECONDS.  THE SAMPLE DATA    *   FILE 047
//*                          FILLS RECORDS 2 THROUGH N.  THE CATCH  *   FILE 047
//*                          IS THAT MONITOR III KEEPS TRACK OF     *   FILE 047
//*                          WHERE THINGS ARE IN THE DATASET BY     *   FILE 047
//*                          USING OFFSET FIELDS THAT ARE RELATIVE  *   FILE 047
//*                          TO BYTE 0 OF RECORD 1. IN EFFECT WHAT  *   FILE 047
//*                          YOU HAVE IS A CHECKPOINTED COPY OF AN  *   FILE 047
//*                          INCORE ARRAY OF SOME KIND, NOTHING IN  *   FILE 047
//*                          RECORDS 2 TO N IS IN ANY NECESSARY     *   FILE 047
//*                          ORDER. THEREFORE, IN ORDER TO PROCESS  *   FILE 047
//*                          THIS MESS YOU NEED THE WHOLE THING IN  *   FILE 047
//*                          CORE.                                  *   FILE 047
//*                                                                 *   FILE 047
//*                          ERB3POST PROCESSES BY READING THE      *   FILE 047
//*                          ENTIRE DATASET INTO MEMORY AND THEN    *   FILE 047
//*                          LOOPING OVER ALL SET OF SAMPLES        *   FILE 047
//*                          POINTERS IN RECORD 1. FOR EACH OF      *   FILE 047
//*                          THESE, TWO SUBROUTINES ARE CALLED ONE  *   FILE 047
//*                          TO PROCESS ASID'S AND ONE TO PROCESS   *   FILE 047
//*                          DEVICES. ASIDS AND DEVICES ARE EACH    *   FILE 047
//*                          HELD IN A TABLE POINTED TO BY THE SET  *   FILE 047
//*                          OF SAMPLES HEADER WHICH IS POINTED TO  *   FILE 047
//*                          FROM RECORD 1. THE SUBROUTINES PRINT   *   FILE 047
//*                          A LINE OF THE REPORT IF THE DELAY      *   FILE 047
//*                          PERCENTS SEEM HIGH AND WRITE A RECORD  *   FILE 047
//*                          TO THE EXTRACT FILES.  THE DATA        *   FILE 047
//*                          WRITTEN TO THE EXTRACT FILES IS        *   FILE 047
//*                          ESSENTIALLY WHAT YOU WOULD SEE WITH    *   FILE 047
//*                          THE "DELAYJ" AND "DEVR" COMMANDS       *   FILE 047
//*                          UNDER RMFWDM.                          *   FILE 047
//*            ENVIRONMENT   MVS/XA 2.1.7                           *   FILE 047
//*                          RMF 3.4                                *   FILE 047
//*                          DFP/XA 2.2                             *   FILE 047
//*            INPUT         A DATASET PRODUCED BY RMF MONITOR      *   FILE 047
//*                          III.                                   *   FILE 047
//*            OUTPUT        A PRINTED REPORT OF JOBS AND DEVICES   *   FILE 047
//*                          WITH HIGH DELAYS                       *   FILE 047
//*                          A SEQUENTIAL FILE, ONE RECORD PER      *   FILE 047
//*                          ASID PER SET OF SAMPLES.               *   FILE 047
//*                          A SEQUENTIAL FILE, ONE RECORD PER      *   FILE 047
//*                          DEVICE PER SET OF SAMPLES.             *   FILE 047
//*                                             - SASGTF -          *   FILE 047
//*            SASGTF   - A SAS PROGRAM TO DECODE GTF SVC TRACE     *   FILE 047
//*                       RECORDS.                                  *   FILE 047
//*                                             - SASHSM -          *   FILE 047
//*            THIS MEMBER CONTAINS 3 SAS PROGRAMS:                 *   FILE 047
//*             HLIST  - READS THE DFHSM CONTROL DATASETS AND       *   FILE 047
//*                      PRINTS REPORTS.  INTENDED TO ANALYZE THE   *   FILE 047
//*                      EFFECTIVENESS OF HSM IMPLEMENTATION.       *   FILE 047
//*             HSMFSR - READS THE "FUNCTION STATISTICS RECORDS"    *   FILE 047
//*                      THAT DFHSM WRITES TO SMF. REPORTS ON       *   FILE 047
//*                      FUNCTIONS THAT DIDN'T WORK, HOW OFTEN      *   FILE 047
//*                      THINGS HAPPENED AND HOW LONG THEY TOOK.    *   FILE 047
//*             HSMLOG - READS THE DFHSM LOG DATASET AND PRINTS     *   FILE 047
//*                      PLOTS OF WHEN THINGS HAPPENED.             *   FILE 047
//*                                            - SASRMF79 -         *   FILE 047
//*            SASRMF79 - A SAS PROGRAM TO PROCESS RMF TYPE 79      *   FILE 047
//*                       RECORDS. SPECIFICALLY IT DEALS WITH       *   FILE 047
//*                       RECORDS PRODUCED BY THE OPTIONS ASD,      *   FILE 047
//*                       SRCS AND SPAG TO PLOT DATA ON 3090        *   FILE 047
//*                       EXTENDED STORAGE USAGE (SUCH LITTLE DATA  *   FILE 047
//*                       AS THERE IS, ANYWAY).                     *   FILE 047
//*                                            - SASSYSLG -         *   FILE 047
//*            SASSYSLG - A SET OF SAS PROGRAMS TO POST-PROCESS     *   FILE 047
//*                       SYSLOG DATA. WE USED THESE TO DESIGN OUR  *   FILE 047
//*                       MPF LIST AMONG OTHER THINGS.              *   FILE 047
//*                                            - SASTLMS -          *   FILE 047
//*            SASTLMS  - A SAS PROGRAM TO REDUCE THE CONTENTS OF   *   FILE 047
//*                       THE TLMSII VOLUME MASTER FILE TO A SAS    *   FILE 047
//*                       DATABASE AND TO PRODUCE A REPORT  FROM    *   FILE 047
//*                       IT ON LOW VOLUME TAPE DATASETS.           *   FILE 047
//*                                            - SMPELIST -         *   FILE 047
//*            SMPELIST - AN ASSEMBLER PROGRAM TO PRODUCE A         *   FILE 047
//*                       SOMEWHAT MORE COMPACT LISTING OF THE      *   FILE 047
//*                       MAC, MOD AND SYSMOD ENTRIES IN AN SMP-E   *   FILE 047
//*                       CSI DATASET.                              *   FILE 047
//*                                                                 *   FILE 047
```
