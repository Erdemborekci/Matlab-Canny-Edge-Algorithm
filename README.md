# Matlab-Canny-Edge-Algorithm 

STEP 1 - READ IMAGE AND CONVERT GRAY LEVEL 
Read the image into MATLAB workspace. Convert the image to gray level. Put the gray level image in your HW report.  

STEP 2 – GAUSSIAN FILTERING  
Filter the gray level image with a 2-D Gaussian smoothing kernel with standard deviation of 𝜎 = 3.  

STEP 3 – COMPUTE THE GRADIENT
Use the following convention for defining x and y axes of the image:
1. Use the appropriate 3x3 Sobel filter to compute the gradient component image 𝐼𝑥 along the x direction. You can use MATLAB’s imfilter function. Use “replicate” for border pixels. Put the gradient component image 𝐼𝑥 in your report. Use imshow(Ix,[]).  
2. Comment on the gradient component image 𝐼𝑥. What do the dark values indicate? What do the bright values indicate?  
3. Use the appropriate 3x3 Sobel filter to compute the gradient component image 𝐼𝑦 along the y direction. You can use MATLAB’s imfilter function. Use “replicate” for border pixels. Put the gradient component image 𝐼𝑦 in your report. Use imshow(Iy,[]).  
4. Comment on the gradient component image 𝐼𝑦. What do the dark values indicate? What do the bright values indicate?  
5. Compute the gradient magnitude image 𝑀. You can use the following command: M = sqrt(Ix.^2+Iy.^2);  
6. Compute the gradient angle image T in degrees. You can use the following command: T = atan2d(Iy,Ix); 

STEP 4 – APPLY NON-MAXIMA SUPPRESSION  
Run the function: gN = myNonMaximaSuppression(M, T);  

STEP 5 – APPLY DOUBLE THRESHOLDING  
1.Run the following code to find the High Threshold (highThresh).  
gN_normalized = gN./max(gN(:));   
m = size(gN_normalized,1);   
n = size(gN_normalized,2);  
PercentOfPixelsNotEdges = 0.99;   
counts=imhist(gN_normalized, 64);   
highThresh = find(cumsum(counts) > PercentOfPixelsNotEdges*m*n, 1,'first') / 64;   
2. Set the Low Threshold to be half of the High Threshold.  
3. Threshold with the Hight Threshold.  
4. Threshold with the Low Threshold.   
