# utl-create-python-panda-dataframe-fow-a-154mb-csv-file-with-60-000-records-an-200-numeric-variables
Create python panda dataframe fow a 154mb csv file with 60,000 records an 200 numeric variables
    Create python panda 154mb  dataframe from a csv file with 60,000 records and 200 numeric variables                                        
                                                                                                                                              
    Are you sure you did not mean 128gb?                                                                                                      
                                                                                                                                              
    github                                                                                                                                    
    https://tinyurl.com/y344538l                                                                                                              
    https://github.com/rogerjdeangelis/utl-create-python-panda-dataframe-fow-a-154mb-csv-file-with-60-000-records-an-200-numeric-variables    
                                                                                                                                              
    I was able to import a 154mb csv file in under 4 seconds with no memory problem.                                                          
                                                                                                                                              
    SOABOX ON                                                                                                                                 
    Since SAS is very expensive, an unbundled business system can easily cost over $10,000 a year,                                            
    I suggest you consider a very inexpensive workstation like mine ($800) with 128gb ram, 32 threads(16 cores) and                           
    NVMe drives.                                                                                                                              
    SOAPBOX OFF                                                                                                                               
                                                                                                                                              
    As a side note Python can read SAS datasets directly. Shouls not have an issue with your tiny dataset.                                    
    If you are dealing with numeric data just create a  binary fiole of IEE floats with SAS                                                   
    and do a binary read in pythton.                                                                                                          
                                                                                                                                              
    I loaded a billion floats into R in less that 15 seconds.                                                                                 
                                                                                                                                              
    see                                                                                                                                       
    https://github.com/rogerjdeangelis/utl_load_1_billion_SAS-floats_into_R_in_13_seconds                                                     
                                                                                                                                              
    Ops text                                                                                                                                  
                                                                                                                                              
    "However, when running some tests today, I was surprised that python ran out of                                                           
    memory when trying to pandas.read_csv() a 128mb csv file. It                                                                              
    had about 200,000 rows and 200 columns of mostly numeric data."                                                                           
                                                                                                                                              
    StackOverflow                                                                                                                             
    https://stackoverflow.com/questions/11622652/large-persistent-dataframe-in-pandas                                                         
                                                                                                                                              
    * create a 152mb csv file of 60,000 records with 200 numeric variables;                                                                   
    Data _null_;                                                                                                                              
      array nums[200] n1-n200 (200*(1.234567890));                                                                                            
      file "d:/csv/have.csv" lrecl=32757 recfm=v;                                                                                             
      do idx=1 to 200;                                                                                                                        
         nam=vname(nums[idx]);                                                                                                                
         put (nam) (',',$4.) @@;                                                                                                              
      end;                                                                                                                                    
      put;                                                                                                                                    
      do rec=1 to 60000;                                                                                                                      
        do idx=1 to 200;                                                                                                                      
           put (nums[idx]) (",",12.9) @@;                                                                                                     
        end;                                                                                                                                  
        put;                                                                                                                                  
      end;                                                                                                                                    
      stop;                                                                                                                                   
    run;quit;                                                                                                                                 
                                                                                                                                              
                                                                                                                                              
    %utl_submit_py64_38('                                                                                                                     
    import pandas as pd;                                                                                                                      
    df = pd.read_csv("d:/csv/have.csv");                                                                                                      
    df.info();                                                                                                                                
    ');                                                                                                                                       
                                                                                                                                              
    NOTE: DATA statement used (Total process time):                                                                                           
          real time           4.61 seconds                                                                                                    
          cpu time            0.07 seconds                                                                                                    
                                                                                                                                              
                                                                                                                                              
    <class 'pandas.core.frame.DataFrame'>                                                                                                     
    RangeIndex: 60000 entries, 0 to 59999                                                                                                     
    Columns: 201 entries, Unnamed: 0 to N200                                                                                                  
    dtypes: float64(201)                                                                                                                      
    memory usage: 92.0 MB                                                                                                                     
                                                                                                                                              
                                                                                                                                              
