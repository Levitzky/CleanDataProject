# This is a Code Book for the Cleaning data course project

- Measurements in this data base are normalised and so unitlless
- All special features (e.g (),-,.) in the variable names were removed

## Pattern names breakdown: 
#### Domain signals:
- time: donates time domain signals
- freq: donates frequency domain signals
#### Raw signals source:
- acc: accelerometer 
- gyro: gyroscope
#### 1st level sub level signals:
- Body
- Gravity
#### 2nd level sub level signals:
- Jerk: Jerk signals
- Mag: magnitude of these three-dimensional signals, calculated using the Euclidean norm 

#### Variables that were estimated from the signals
- mean: Mean value
- std: Standard deviation
#### XYZ 
denote 3-axial signals in the X, Y and Z directions

## Activity types
1 WALKING
2 WALKING_UPSTAIRS
3 WALKING_DOWNSTAIRS
4 SITTING
5 STANDING
6 LAYING

## Tidy data set variable names (column names):
 [1] "Subject" - An identifier of the subject (volunteer) who carried out the experiment                          
 [2] "Activity" - descriptive name of activity                       
 [3] "timeBodyAccmeanX"                 
 [4] "timeBodyAccmeanY"                 
 [5] "timeBodyAccmeanZ"                 
 [6] "timeGravityAccmeanX"              
 [7] "timeGravityAccmeanY"              
 [8] "timeGravityAccmeanZ"              
 [9] "timeBodyAccJerkmeanX"             
[10] "timeBodyAccJerkmeanY"             
[11] "timeBodyAccJerkmeanZ"             
[12] "timeBodyGyromeanX"                
[13] "timeBodyGyromeanY"                
[14] "timeBodyGyromeanZ"                
[15] "timeBodyGyroJerkmeanX"            
[16] "timeBodyGyroJerkmeanY"            
[17] "timeBodyGyroJerkmeanZ"            
[18] "timeBodyAccMagmean"               
[19] "timeGravityAccMagmean"            
[20] "timeBodyAccJerkMagmean"           
[21] "timeBodyGyroMagmean"              
[22] "timeBodyGyroJerkMagmean"          
[23] "freqBodyAccmeanX"                 
[24] "freqBodyAccmeanY"                 
[25] "freqBodyAccmeanZ"                 
[26] "freqBodyAccJerkmeanX"             
[27] "freqBodyAccJerkmeanY"             
[28] "freqBodyAccJerkmeanZ"             
[29] "freqBodyGyromeanX"                
[30] "freqBodyGyromeanY"                
[31] "freqBodyGyromeanZ"                
[32] "freqBodyAccMagmean"               
[33] "freqBodyAccJerkMagmean"           
[34] "freqBodyGyroMagmean"              
[35] "freqBodyGyroJerkMagmean"          
[36] "angletBodyAccmeangravity"         
[37] "angletBodyAccJerkmeangravityMean" 
[38] "angletBodyGyromeangravityMean"    
[39] "angletBodyGyroJerkmeangravityMean"
[40] "angleXgravitymean"                
[41] "angleYgravitymean"                
[42] "angleZgravitymean"                
[43] "timeBodyAccstdX"                  
[44] "timeBodyAccstdY"                  
[45] "timeBodyAccstdZ"                  
[46] "timeGravityAccstdX"               
[47] "timeGravityAccstdY"               
[48] "timeGravityAccstdZ"               
[49] "timeBodyAccJerkstdX"              
[50] "timeBodyAccJerkstdY"              
[51] "timeBodyAccJerkstdZ"              
[52] "timeBodyGyrostdX"                 
[53] "timeBodyGyrostdY"                 
[54] "timeBodyGyrostdZ"                 
[55] "timeBodyGyroJerkstdX"             
[56] "timeBodyGyroJerkstdY"             
[57] "timeBodyGyroJerkstdZ"             
[58] "timeBodyAccMagstd"                
[59] "timeGravityAccMagstd"             
[60] "timeBodyAccJerkMagstd"            
[61] "timeBodyGyroMagstd"               
[62] "timeBodyGyroJerkMagstd"           
[63] "freqBodyAccstdX"                  
[64] "freqBodyAccstdY"                  
[65] "freqBodyAccstdZ"                  
[66] "freqBodyAccJerkstdX"              
[67] "freqBodyAccJerkstdY"              
[68] "freqBodyAccJerkstdZ"              
[69] "freqBodyGyrostdX"                 
[70] "freqBodyGyrostdY"                 
[71] "freqBodyGyrostdZ"                 
[72] "freqBodyAccMagstd"                
[73] "freqBodyAccJerkMagstd"            
[74] "freqBodyGyroMagstd"               
[75] "freqBodyGyroJerkMagstd"   
