# Development of a multiple stereo-camera system (in C++) for generating datasets to train neural networks
This is the project for my master's thesis on Faculty of mechanical engineering and naval architecture in Zagreb.       

I have used libraries: OpenCV, PCL, Open3D, Eigen, liberalsense(for RealSense cameras) etc. in C++.          

This project shows some 2D filtering and more 3D operations over point cloud like: Crop, Estimate normals, Axis aligned bounding box, Paint uniform, Remove radius outliers, Remove statistical outliers, Select by index, transform, Voxel down sample...       

**The whole C++ code is visible in main.cpp**   It's still under development!           


## Project workflow

#### 1. Design and make a laboratory setup with three Intel RealSense D435 cameras.      
I have designed camera mounters in CATIA v5 and printed them out on 3D printer.
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/167845597-a045333a-baa1-4c78-bd2a-e993177bfe81.png" />
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/167845633-7793631e-af89-4836-9aa9-8ab96b884bf6.png" />
</p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/167847945-50d6187c-d999-4552-99e9-e49f93237d7a.jpeg" />
</p>



#### Step 2. Single camera calibration  
Each camera has to be calibrated. Here is an example of (one of) a picture taken for the process.     
All 9 pictures taken are in folder **cam1_calibration_images**(or Cam2, Cam3).
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/167884116-37fb5a6c-d193-4bfb-9711-a0eff424f1a1.png" />
</p>



#### Step 3. Stereo calibration      
This is the same picture of space taken from 2 cameras in order to get their extrinsic Rotation and Translation.
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/168120467-29f5d0e6-c4bc-46de-bc67-1c75a51ec282.png" />
</p>

Result is Transformation Matrix between two cameras:
![Screenshot_8](https://user-images.githubusercontent.com/96240235/168126552-b9d432ce-4800-406d-a770-56bad94c373a.png)



#### Step 4. Taking frames and converting them in 2D pictures and 3D point clouds    
Code can be seen in **saveframes** function in main.cpp



#### Step 5. 2D pictures filtering      
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/168118883-9ef7aa84-80a9-4e18-8d1b-a142795b9cd8.png" />
</p>



#### Step 6. 3D point cloud filtering
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/168124090-e2c32eb9-e0ed-436b-8a0a-4c3ff4ddbd6f.png" />
</p>



#### Step 7. 3D point clouds stitching      
Using stereo calibrated extrinsic coefficients and ICP (Iterative Closest Points) to stith together clouds from 3 stereo cameras.      
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/168130619-2839153d-c9ac-4153-a5b9-28efc9f92616.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/168130623-115d017a-4a66-4f7b-bc00-979d64668ac9.png" />
</p>


##### Cedevita example       
###### 1 Frame taken from each camera
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170508418-3d217042-edad-43a8-87ec-b5bc71097999.png" />
</p>

###### After Stereocalibration registration
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170508429-2ef862f6-f905-4a61-8dbc-eed730cd5ccf.png" />
</p>

###### After ICP registration
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170508440-737e9840-ca46-47c1-b5f9-7051f6db396a.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170508452-2b3280b6-0697-41ba-bfad-609fa261f782.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170508467-472a8cd5-6e9f-4c38-add8-cebd24559e04.png" />
</p>



#### Step 8. 2D pictures labeling with Roboflow    
<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170505975-4f10f13d-1837-4c91-a559-23f6a85702ab.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170506128-3b8cee76-ea8e-4476-8447-c4d83d080374.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170506281-2a87de29-5d90-4787-9940-c490c7468c20.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/96240235/170506304-a0e11c64-f3f3-4a80-9926-02cd67b77f32.png" />
</p>


#### Step 9. Object detection with YOLOv5  

<p align="center">
<img src="https://user-images.githubusercontent.com/96240235/170451802-c7cdcf6b-172a-42a6-8f05-d424099d1e6d.gif" alt="Databay showcase gif" title="Databay showcase gif" width="500"/> 
</p>

