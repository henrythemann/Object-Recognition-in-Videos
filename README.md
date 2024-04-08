## Identifying Objects in Videos

### Executive Summary
**Project Overview and Objectives**
The primary objective of this project is to develop a computational model capable of recognizing diverse types of objects within video streams. This endeavor is critical in the context of autonomous vehicle technology, a domain witnessing significant investment from leading technology corporations. For autonomous vehicles, the capacity for precise object detection from video inputs is crucial, marking the boundary between safety and peril for pedestrians and other vehicles.

**Key Findings**
Through the implementation of a UNet architecture, the project achieved a validation accuracy of 84.53% in object label prediction. This result represents a promising step forward in the field of video-based object recognition.

### Rationale
The development of robust and efficient object recognition models for video data is foundational to advancing autonomous navigation systems, especially in the context of self-driving vehicles. These systems require real-time interpretation of dynamic environments to make instantaneous decisions that ensure safety and compliance with traffic laws. The complexity of video data, characterized by its temporal continuity and the variability in object appearance due to changes in perspective, lighting, and occlusion, necessitates sophisticated modeling techniques that can accurately and efficiently process this information. The choice of UNet as the primary model architecture is motivated by its proven effectiveness in semantic segmentation tasks, which is analogous to assigning labels to each pixel in an image, or in this case, frames of a video.

### Data Sources
This project leverages a dataset obtained from Kaggle, specifically the "CamVid" database (https://www.kaggle.com/datasets/carlolepelaars/camvid). The dataset comprises 4 videos, split into image sequences, with each image sequence split between the test, train, and validation set. The labels are annotated with object class semantic labels, enriched with metadata to facilitate a comprehensive evaluation of emerging algorithms. Each pixel in the dataset images is associated with one of 32 predefined semantic classes, making the dataset particularly suitable for training models in the context of autonomous driving. The videos, captured from the perspective of a moving vehicle, offer a rich variety of object classes and scenarios, simulating the real-world conditions that autonomous vehicles must navigate. A subset of 369 still frames from this dataset serves as the basis for model training.

[![output.png](https://i.postimg.cc/nhJp3Dpz/output.png)](https://postimg.cc/zV0sB3LZ)

### Methodology
The project employed a structured approach to CNN model development, starting with data preprocessing to normalize input frames and segregate them into training and validation sets. Given the UNet model's architecture, known for its effectiveness in image segmentation tasks, we adapted it for video frame analysis by treating each frame as a standalone image. The model architecture comprises an encoder path to capture context and a symmetric decoder path that enables precise localization, making it well-suited for the task at hand.

Training involved the use of a cross-entropy loss function, optimized with an Adam optimizer, reflecting a balance between learning efficiency and computational resource considerations. The choice of a validation accuracy metric facilitated an objective assessment of model performance, guiding iterative refinements.

### Model evaluation and results 
The UNet model was constructed with a downsampling path, a bottlenech, and an upsampling path. Initially, with 64 base filters and the default learning rate of 0.001, the model was only able to achieve a 79.82% validation accuracy. 

[![double-filter-sizes-val-acc-7982.png](https://i.postimg.cc/zvw8Nzk5/double-filter-sizes-val-acc-7982.png)](https://postimg.cc/xNdWyS7F)

After executing a hyperparameter search, it was discovered that 192 base filters and a learning rate of 0.0006 performed better. With these updated hyperparamters, the model was able to achieve a validation accuracy of 84.53%.

[![after-hyperparameter-optimization.png](https://i.postimg.cc/d0gW98cN/after-hyperparameter-optimization.png)](https://postimg.cc/cKMMxtHf)

### Next Steps
To advance the project, a comparative analysis with alternative models such as ConvLSTM, 3D Convolutional Networks, and Temporal Convolutional Networks (TCN) is proposed. These models offer different approaches to capturing temporal dynamics in video data, potentially enhancing object recognition accuracy and efficiency.

### Conclusion
The project underscores the significant challenges and resource demands associated with developing real-time object recognition systems for autonomous vehicles. Despite the promising results achieved with the UNet model, the constraints posed by hardware limitations and the necessity for real-time processing highlight the need for continued innovation in model architecture and optimization strategies. Achieving a balance between computational efficiency and model effectiveness remains a pivotal challenge in making autonomous vehicles a viable and safe option for consumers.