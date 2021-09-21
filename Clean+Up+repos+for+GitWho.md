# Clean Up repos for GitWho

# ![](./media/image1.tmp)**Needs works, still in redaction\!**

Make a backup:

Fork the repository to GEDA

![](./media/image2.tmp)

Select "GED Archive". You may rename the repository. Un-select the sync.

![](./media/image3.tmp)

Click "Fork repository"

# Clone the repository

 It's recommended to use "SourceTree";

![](./media/image4.tmp)

For manual deletion, right on remote.....

![](./media/image5.tmp)

# Batch deletion of merged branches

Open a "bash" shell,....

TDSECURITIES+buczym2@WIND00435436 MINGW64 /d/dev/sophisweb2  (master)
                                                               
$ git branch -r --sort=-committerdate --merged | sed 's/^
\*origin\\///'| grep -v ^master$ |grep -v '^HEAD ' |sed '1,/^develop$/d'

if return nothing use:

TDSECURITIES+buczym2@WIND00435436 MINGW64 /d/dev/sophisweb2  (master)
                                                          
$ git branch -r --sort=-committerdate --merged | sed 's/^
\*origin\\///'| grep -v ^master$ |grep -v '^HEAD ' |grep -v ^develop$  
release/20.3.4
                                                                                                               
feature/GEDTECH-4488
                                                                                                         
feature/GEDTECH-4386
                                                                                                         
feature/jenkins-choco-testing
                                                                                                
hotfix/20.2.2.1
                                                                                                              
feature/GEDTECH-4354
                                                                                                         
release/20.1.2
                                                                                                               
feature/deleting-master
                                                                                                      
hotfix/19.12.2.1
                                                                                                             
feature/GEDTECH-4145\_NEW1
                                                                                                    
release/19.11.2
                                                                                                              
release/19.9.4
                                                                                                               
feature/GEDTECH-3765-jenkins-automation
                                                                                      
feature/DivDeleteAddition
                                                                                                    
feature/packageBookingFix
                                                                                                    
feature/GEDDEV-863
                                                                                                           
feature/GEDDEV-861-fix-sophis-toolkit-nuget-package-especially-for-sophisweb2
                                                
feature/GEDTECH-3461-re-balancing-all-services-on-prod-servers
                                                               
release/19.5.3
                                                                                                               
feature/wcfCleanup
                                                                                                           
feature/GEDTECH-3190-positioncash-and-coherency
                                                                              
feature/GEDTECH-3153-rt-and-position-service-in-hydra-2
                                                                      
feature/GEDTECH-3206
                                                                                                         
feature/owinUsers
                                                                                                            
feature/bookingCodeNodeRemoval
                                                                                               
feature/bookingCodeNodeRemove
                                                                                                
feature/marketData
                                                                                                           
feature/risk-engine-rt
                                                                                                       
feature/get-calls-without-code   

So redirect to a file the right command, in ours case the second:

TDSECURITIES+buczym2@WIND00435436 MINGW64 /d/dev/sophisweb2  (develop)
                                                                           
$ git branch -r --sort=-committerdate --merged | sed 's/^
\*origin\\///'| grep -v ^master$ |grep -v '^HEAD ' |grep -v ^develop$
\>merged-list.txt

edit the file remove the brnaches that you whnat to kept and run:

TDSECURITIES+buczym2@WIND00435436 MINGW64
/d/dev/sophisweb2 (develop)                      
$ cat merged-list.txt | xargs -n 1 git push --delete origin
                               
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-4488
                                                 
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-4386
                                                 
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/jenkins-choco-testing
                                        
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         hotfix/20.2.2.1
                                                      
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-4354
                                                 
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         release/20.1.2
                                                       
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/deleting-master
                                              
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         hotfix/19.12.2.1
                                                     
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-4145\_NEW1
                                            
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         release/19.11.2
                                                      
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         release/19.9.4
                                                       
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-3765-jenkins-automation
                              
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/DivDeleteAddition
                                            
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/packageBookingFix
                                            
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDDEV-863
                                                   
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]
        feature/GEDDEV-861-fix-sophis-toolkit-nuget-package-especially-for-s  
ophisweb2
                                                                                 
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]
        feature/GEDTECH-3461-re-balancing-all-services-on-prod-servers
       
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         release/19.5.3
                                                       
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/wcfCleanup
                                                   
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-3190-positioncash-and-coherency
                      
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]
        feature/GEDTECH-3153-rt-and-position-service-in-hydra-2
              
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/GEDTECH-3206
                                                 
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/owinUsers
                                                    
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/bookingCodeNodeRemoval
                                       
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/bookingCodeNodeRemove
                                        
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/marketData
                                                   
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/risk-engine-rt
                                               
To <ssh://bitbucket.tds.td.com:7999/gedtwo/sophisweb2.git>
                                  
 - \[deleted\]         feature/get-calls-without-code  

TDSECURITIES+buczym2@WIND00435436 MINGW64
/d/dev/sophisweb2 (develop)                      
$ rm merged-list.txt
