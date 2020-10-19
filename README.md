![Sin titulo](http://atvs.ii.uam.es/atvs/github/mEBAL/mEBAL_ICONO1.jpg)
***
# About
We present mEBAL, a multimodal database for eye blink detection and attention level estimation. mEBAL is a database which is initially introduced in [arXiv technical report](https://arxiv.org/abs/2006.05327) and then accepted by the [22nd ACM International Conference on Multimodal Interaction](http://icmi.acm.org/2020/). 

The eye blink frequency is related to the cognitive activity and automatic detectors of eye blinks have been proposed for many tasks including attention level estimation, analysis of neuro-degenerative diseases, deception recognition, drive fatigue detection, or face anti-spoofing. However, most existing databases and algorithms in this area are limited to experiments involving only a few hundred samples and individual sensors like face cameras. 

The proposed mEBAL improves previous databases in terms of numbers samples in eye blink and cognitive information available.  In particular, **three different sensors** are simultaneously considered: **Near Infrared (NIR)** and **RGB cameras** to capture the face gestures and an **Electroencephalography (EEG) band** to capture the cognitive activity of the user and blinking events.

Regarding the size of mEBAL, it comprises **6,000 samples** and the corresponding **attention level** from **38 different students** while conducting a number of e-learning tasks of varying difficulty.**This information is avalible on this web [[Download Database](#instructions-for-downloading-edBB)].**

The following table shows the sensors and the information captured:

![Sin titulo](http://atvs.ii.uam.es/atvs/github/mEBAL/TABLE_SENSORS.jpg)


<br/>The following sections describe the motivation, the activities designed, the sensors, the public database and share mEBAL database with the community to advance in this area:

# Motivation

The main motivation  of this work is  **the improvement of the virtual education** using e-learnig platforms. Virtual education technologies are growing up, with a market reaching a turnover around 240.000 million dollars. 
**E-learning platforms** are important tools to get high quality online education. They allow to capture student information to better understand the student behavior and conditions and this information can be used to create personalized environments. Information such as the heart rate, the emotional state, or the cognitive activity can be used to improve e-learning platforms.
Undoubtedly, e-learning platforms will benefit significantly by exploiting the **attention level** of the student. This could be used to: **i)** adapt dynamically the environment and content  based on the attention level, and **ii)** improve the educational materials and resources with a posterior analysis of the e-learning sessions (e.g. detecting the type of contents more appropriate for a specific student).

**Since the 70s there are studies relating the eye blink rate with cognitive activity like attention**. The studies suggest that **lower eye blink rates** can be associated to **high attention** periods while **higher eye blink rates** are related to **low attention levels**. Therefore, in this context, automatic eye blink detection can be a tool for estimating the attention level of the students and improving e-learning platforms.

For this reasons, we hope that mEBAL will be valuable to the scientific community thanks to the multimodal nature: **Cognitive Activity and Eye Blink detection**.

# Sensors

   The acquisition setup consisted of the next components: 

   - 3 individual **RGB cameras** (frontal, side, and cenital), and 1 **Intel Real-Sense** (model D435i), which is composed by 1 RGB and 2 Near Infrared sensors, and which also computes also depth images combining its 3 image channels.

   - A **Huawei Watch 2** that captures pulse information in real time and has also accelerometer, magnetometer, and gyroscope; useful to measure the arm movements.


   - An **EEG headset** by NeuroSky that captures 3 channels of electroencephalogram information. These data can be employed to know the focus level, stress, vigilance, etc. of the students
  
   - A **Personal Computer** with Microsoft Windows 10 OS, a microphone to acquire audio, a regular keyboard, a mouse, and a screen. The computer is employed both to complete the tasks and also to acquire the screen data, the mouse and keyboard dynamics, audio information during the evaluation, and several types of metadata (e.g. logging, app and web history, IP and MAC addresses, etc.)


# Tasks


The activities designed to conform the database consist of 8 different tasks that can be categorized in the following three groups:
 
 - **Enrollment form:** Its target consists in obtaining personal data of the users such as their name and surname, ID number, nationality, e-mail address, etc. This form is designed to acquire different events such as the mouse dynamics, clicks, mouse wheel, keyboard use, etc.
 
 - **Writing questions:** These comprehend questions that require a complex interaction from the user. They are oriented to measure the students’ cognitive abilities under different situations such as: solving logical problems, describing images, crosswords, finding differences, etc. Additionally, some activities have been designed to induce different states of emotions to the participants, e.g. stress or nervousness. These altered states are highly relevant when working with physiological and biological signals.
 
 - **Multiple choice questions:** These are questions aimed to detect the students’ attention and focus levels. Since multiple choice exams are largely used in online assessment platforms to evaluate their students, including these in our evaluation was essential.

The questions are selected from popular riddles and they present different levels of difficulty. The interface is designed to ensure data from different nature: free text typing (writing questions), fixed text typing (enrollment form), mouse movement (multiple choice questions), visual attention (describing images and finding differences), etc.


# Database and Challenges

The initial subset of the full database that is released with the present paper is composed by 20 users captured under controlled laboratory conditions during one session. The enrollment form includes demographic information from the user (age, gender, right-handed or left-handed). Additionally, we provide the performance (accuracy and time) achieved by each user in each specific task. Together with
the raw data obtained from the sensors, the database includes information processed to better understand and model the student behavior. This information is obtained using stateof-the-art algorithms:

- **Head Pose:** head pose (pitch, roll, and yaw) is estimated from the frontal webcam using the algorithm proposed in [1].

- **Mental State:** attention and meditation is estimated from the EEG signals according to the method developed by NeuroSky. The attention indicates the intensity of mental “focus”. The value ranges from 0 to 100. The attention level increases when a student focuses on a single thought or an external object, and decreases when distracted. The meditation indicates the level of mental relaxation. The value ranges from 0 to 100, and increases when users relax the mind and decreases when they are uneasy or stressed.

- **Face Biometrics:** size of the face (related to the distance to the front webcam) and authentication score are provided using the face detection algorithm proposed in [2] and the face authentication model [3].

Next figure shows an example of the information captured during the execution of the tasks:

![Sin titulo ](http://atvs.ii.uam.es/atvs/github/imagen_articulo.jpg)

We have designed an acquisition protocol incorporating all sensors presented in the previous sections.Some of the sensors are used to capture the groundtruth for the different challenges proposed. **We propose 5 challenges related to the monitorization of different behaviors relevant for e-learning platforms.**

For each challenge, we propose target and input data. The goal is to train new artificial intelligence models capable of predicting the
target from the input data.
**The 5 challenges proposed in this work are:** 

- **Challenge 1 - Attention Estimation:** an estimation of the attention level of the students during the execution of e-learning tasks is a very valuable resource. We propose to estimate the band signals (level of attention) from patterns captured from the basic sensors. The head pose and gaze estimation from the webcam, together with the mouse and keystroke dynamics can be used to predict attention of the students. **Target:** attention level obtained from the band signals. **Input:** front webcam video, mouse, and keystroke
sequences. [[Download Challenge 1](http://)]

- **Challenge 2 - Anomalous Behavior Detection:** the detection of non-allowed behaviors during the execution of evaluation tasks is an important challenge necessary to improve the trustworthiness in e-learning platforms. Ten users were instructed to perform non-allowed activities during the execution of the tasks. These activities comprise the use of material/resources with the correct responses to the questions. We propose the use of a smartphone as a non-allowed resource. These users try to hide the smartphone in their pockets. These events are labelled with a timestamp that identify the exact period when cheating really occurred.. We propose to use the basic sensors to detect these events. **Target:** detection of nonallowed events. **Input:** front webcam video, microphone, mouse, and keystroke dynamics. [[Download Challenge 2](http://)]
<br/><br/>The following image shows an example of this challenge:


<p align="center"><img src="http://atvs.ii.uam.es/atvs/github/CHALLENGE.png"></p>

- **Challenge 3 - Performance Prediction:** each task is evaluated and the performance is measured in terms of
accuracy (percentage of correct responses) and time spent to complete the task. We propose to estimate the performance of the student using both basic and advance sensors. **Target:** accuracy. **Basic Input:** front webcam video, mouse, and keystroke. **Advanced Input:** basic sensors plus pulse and EEC band signals. [[Download Challenge 3](http://)]

- **Challenge 4 - User Authentication:** student authentication is a critical step in a e-learning platforms. All users complete the same tasks, including the enrollment form that contains personal data. Data is anonymized but an ID number is provided to identify data from each user. The dataset is rich in biometric patterns useful for authentication (face, keystroke, mouse). **Target:** identity of the student. **Basic Input:** front webcam video, mouse, and keystroke dynamics. **Advanced Input:** IR cameras, smartwatch sensors, EEG band. [[Download Challenge 4](http://)]

- **Challenge 5 - Pulse Estimation:** the pulse is highly related to the emotional state and stress level of the students. In this challenge, we propose to estimate the pulse from the smartwatch using the front camera. Alternatively, the IR cameras can be used to analyse the potential of these sensors. **Target:** pulse of the student. **Basic Input:** front webcam video. **Advanced Input:** IR cameras. [[Download Challenge 5](http://)]


# Download

The information is available at the following links:

- **The initial subset of the full database** [[link](http://)]. 

- **Challenge 1.** Input data and processed data [[link](http://)].  [[TXT file](http://)] includes information about the challenge and the target proposed.

- **Challenge 2.** Input data and processed data [[link](http://)].  [[TXT file](http://)] includes information about the challenge and the target proposed.

- **Challenge 3.** Input data and processed data [[link](http://)].  [[TXT file](http://)] includes information about the challenge and the target proposed.

- **Challenge 4.** Input data and processed data [[link](http://)].  [[TXT file](http://)] includes information about the challenge and the target proposed.

- **Challenge 5.** Input data and processed data [[link](http://)].  [[TXT file](http://)] includes information about the challenge and the target proposed.





# License

Any entity using this dataset agrees to the following conditions:

THIS DATASET IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



# References

[1] Ruiz, N.; Chong, E.; and Rehg, J. M. 2018. Fine-Grained Head Pose Estimation Without Keypoints.


[2] Zhang, K.; Zhang, Z.; Li, Z.; and Qiao, Y. 2016. Joint face detection and alignment using multi-task cascaded convolutional networks. *IEEE Signal Processing Letters* 23(10):1499–1503.

[3] Cao, Q., et al. 2018. VGGFace2: A dataset for recognising faces across pose and age.


# Contact:

For more information contact Aythami Morales, associate professor UAM at aythami.morales@uam.es

