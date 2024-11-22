# RobotV_Grab-box
Robot arm grabbing cardboard boxes in disordered scenes

The main code location is \ultralytics-main\pyorbbecsdk-main\examples\main.py

Gemini2 camera configuration:

SDK Download：https://developer.orbbec.com.cn/develop_details.html?id=1

Related environment configuration instructions: https://vcp.developer.orbbec.com.cn/documentation

Initialize and configure the camera startup

![image](https://github.com/user-attachments/assets/ad5d45ae-e041-4353-9f66-b36bb75f6ebb)

Then enter the loop for real-time object detection

![image](https://github.com/user-attachments/assets/a895b55e-9b2b-4ec6-a440-5e48f910eb58)

Applying the results of object detection to the pose estimation network,In order to facilitate the adaptation of point cloud size to match the size of the detected image, it is necessary to change the cpp configuration file of the SDK to obtain all pixel point clouds，The modification is located in lines 320-322 of \ ultralytics main \ pyrgbecsdk main \ src \ pyrgbecsdk \ fram.cpp，Annotate the zero point cloud filtering code and re create the cmake SDK.

![image](https://github.com/user-attachments/assets/d335b13c-6ce9-410b-b8fe-45f44383074d)

Input the camera RGB image, point cloud detection image, and object detection box results into the pose estimation network for calculation:

![image](https://github.com/user-attachments/assets/09a7a030-2e7f-4fee-902d-ada3430c9d0a)

Link Card Robot SDK:

Linux needs to put libjakaAPI.so and jkrc.so in the same folder, and add the current folder path to the environment variable, export LD_LIBRRY-PATH=/xx/xx/, and call the section card SDK to fetch them.
