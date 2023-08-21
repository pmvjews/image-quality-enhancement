
![iqe](https://github.com/pmajews/best_tennis_players_recognition/assets/83170837/e518197f-28a4-491f-91a0-e0f21ec03cad)


## Description

The "Image Quality Enhancement" project is an advanced image processing initiative aimed at significantly improving the visual quality of low-resolution images. By leveraging cutting-edge deep learning techniques, specifically Super-Resolution Generative Adversarial Networks (SRGANs), this project aims to enhance image details, sharpness, and overall quality, resulting in strikingly improved visual content.

## Dataset

The dataset used for training and testing the model is the [MIRFLICKR-1M](https://press.liacs.nl/mirflickr/mirdownload.html), with 60 000 images (only a small portion of the entire dataset was downloaded). The dataset consists of two primary categories of images: high-resolution images and low-resolution images.

## Exploratory data analysis
### Distribution of Original Image Sizes

The dataset consists of images sourced from various contexts, displaying a range of dimensions. Notably, a substantial portion of the images align with a size of 500x500 pixels, showcasing a prevalent standard. This size indicates a commonality in image content or capture. While 500x500 pixel images dominate, the dataset maintains diversity in sizes, enhancing the model's generalization capabilities.
![distribution_of_image_sizes](https://github.com/pmajews/dog_breed_recognition/assets/83170837/4e0c1456-360e-4480-aa0a-85e7c12f102b)

### High-Resolution Images

The high-resolution images in the dataset possess dimensions of 256x256 pixels. These images have been carefully curated to provide detailed and fine-grained visual information.
![hr_images_grid](https://github.com/pmajews/dog_breed_recognition/assets/83170837/30c0df9f-3ba8-429b-b05b-c968b756739e)
### Low-Resolution Images

The low-resolution images, on the other hand, have been generated by resizing the high-resolution images to dimensions of 64x64 pixels. This resizing process reduces the spatial resolution of the images, resulting in a loss of finer details. The purpose of including low-resolution images in the dataset is to simulate scenarios where the model encounters images with reduced quality or resolution. This is particularly relevant in applications where computational efficiency or low-quality input data may be a concern.
![lr_images_grid](https://github.com/pmajews/dog_breed_recognition/assets/83170837/dff9a03d-6efd-4fb1-833f-d7265698aa53)
### Preprocessing Steps

The creation of the low-resolution images involved a preprocessing step where the high-resolution images were simply resized using numpy library to achieve the target dimensions of 64x64 pixels. It's important to note that this resizing process inherently leads to a loss of information, as the high-frequency details present in the original images cannot be fully retained.

**High-Resolution Images**
The preprocessing applied to the high-resolution images was limited to resizing them to dimensions of 256x256 pixels. This resizing step was carried out to standardize the dimensions of the images and ensure compatibility with the model's architecture and training process. No additional modifications, such as noise reduction or contrast enhancement, were applied to the high-resolution images, allowing them to retain their original quality and detail.

The availability of both high-resolution and low-resolution images within the dataset enables the model to learn to bridge the gap between different levels of image quality and resolution. This learning is crucial for that project.

## Model training

The heart of that machine learning project lies in the process of training a deep learning model that can enhance the quality of images. In pursuit of this goal, **SRGAN (Super-Resolution Generative Adversarial Network)** architecture has been applied, which is a state-of-the-art solution designed specifically for image super-resolution tasks.

### SRGAN Architecture: Elevating Image Quality

The choice of the SRGAN architecture was driven by its remarkable ability to elevate the quality of images through an ingenious combination of **generative adversarial networks (GANs)** and **deep convolutional neural networks (CNNs)**. The architecture's inherent capacity to generate high-resolution images from low-resolution counterparts aligns seamlessly with our project's objective of improving image quality.

**SRGAN consists of two key components:** the generator network and the discriminator network. The generator takes low-resolution images as input and progressively transforms them into high-resolution images with exceptional clarity. This process is guided by a perceptual loss function that encourages the generated images to closely match the target high-resolution images in both content and structure. This perceptual loss is computed using a pre-trained feature extractor, typically derived from a convolutional neural network, such as **VGG19**.

The discriminator, on the other hand, is responsible for distinguishing between genuine high-resolution images and those generated by the generator. This adversarial interplay between the generator and the discriminator drives the training process, pushing the generator to create high-quality images that are increasingly difficult to distinguish from real high-resolution images.

##### Training Strategy and Data Preparation

To train SRGAN model, a comprehensive dataset consisting of high-resolution images was prepared. These images were paired with their downsampled low-resolution counterparts, simulating real-world scenarios where enhancing image quality is crucial. During training, the model learns to bridge the gap between low and high resolutions, gradually acquiring the ability to generate images that are both visually appealing and faithful to the original high-resolution content.

The training process involves iteratively optimizing both the generator and discriminator networks. The generator strives to minimize the perceptual loss while fooling the discriminator, while the discriminator endeavors to accurately classify genuine high-resolution images and generated images.

##### Benefits and Implications

The adoption of the SRGAN architecture offers several benefits and implications for our project:

**Enhanced Visual Quality:** The SRGAN architecture holds the promise of significantly enhancing the visual quality of images, making them more suitable for various applications and use cases.

**Realistic Image Enhancement:** By leveraging adversarial training, SRGAN produces images that not only possess higher resolution but also maintain a level of realism and detail that goes beyond simple interpolation techniques.

**Transferability:** The knowledge gained from training the SRGAN model on our specific dataset can potentially be transferred to related tasks, such as image denoising and inpainting, broadening the scope of our project's impact.

In conclusion, the selection of the SRGAN architecture as the foundation of our image enhancement project underscores  commitment to leveraging cutting-edge techniques to achieve objective of improving image quality.

##### Model Architecture Alignment
Model architecture closely follows the structure outlined by the original SRGAN paper, maintaining the core components of the generator and discriminator networks. By adhering to this well-established architecture, we benefit from the insights and innovations that have emerged through rigorous research and experimentation.

![srgan_architecture](https://github.com/pmajews/dog_breed_recognition/assets/83170837/07427ec6-76d1-476d-81ef-75a8f8cd7bab)

### Training Process and Model Limitations
The training of the Super-Resolution Generative Adversarial Network (SRGAN) is a complex and iterative process that aims to enhance the visual quality of images by generating high-resolution counterparts from low-resolution input. The chosen architecture, SRGAN, holds the promise of achieving remarkable results through a combination of generative adversarial networks (GANs) and deep convolutional neural networks (CNNs).

The training process spanned a duration of 5 days, during which the SRGAN model was exposed to a dataset comprising 12,500 pairs of high-resolution and low-resolution images. These paired images play a pivotal role in teaching the model to bridge the gap between varying levels of image quality and resolution. Each iteration of training involved optimizing two key components: the generator and the discriminator networks.

The generator network, often referred to as the "heart" of the SRGAN architecture, undertakes the task of transforming low-resolution input images into high-resolution counterparts. This transformation process is driven by a perceptual loss function that encourages the generated images to align with the target high-resolution images in terms of content and structure. This function leverages a pre-trained feature extractor, usually derived from a convolutional neural network such as VGG19.

Complementing the generator, the discriminator network plays a critical role in distinguishing between genuine high-resolution images and those generated by the generator. This adversarial interplay between the generator and discriminator drives the training process. The generator strives to minimize the perceptual loss while simultaneously outwitting the discriminator, which, in turn, aims to accurately classify real high-resolution images from the generated ones.

However, it's important to acknowledge that the achieved model, while promising, is not without its limitations. The primary constraint stems from the available computational resources, specifically the GPU utilized for training. Despite the robust architecture and the extensive training duration, the model's performance is constrained by these resource limitations. It's important to note that, given more computational power and time, the model's quality and capabilities could potentially be further enhanced.


### Deployment with Docker:

**Docker Images:** The project consists of two Docker images, one for the backend server and another for the frontend interface. The backend image contains the Flask-based server that handles image processing, while the frontend image provides the user interface for interaction.

**Docker Compose File:** The Docker Compose file is utilized to orchestrate the deployment of both containers. It defines the services, builds, ports, and environment variables required for the project to run smoothly.

**Local Deployment:** Using the ```docker-compose up ``` command, the local deployment of the project is initiated. The backend and frontend containers are built and started, enabling users to access the project locally through their browser.

### Deployment on Google Cloud with Kubernetes:

![gcp_deploy](https://github.com/pmajews/best_tennis_players_recognition/assets/83170837/645860d1-ee9c-4325-9a2f-accde6f64caf)

**Kubernetes Deployment:** To further explore the capabilities of container orchestration, the project is deployed on Google Cloud using Kubernetes. This step involves creating a Kubernetes deployment configuration that specifies the number of replicas, image details, and resource allocation.

**Kubernetes Services:** A Kubernetes Service is defined to expose the deployed application to external traffic. The Service allows users to access the SRGAN project using a publicly accessible IP address.

**Google Cloud Platform:** The Kubernetes cluster is created on the Google Cloud Platform (GCP), utilizing GCP's Kubernetes Engine. This enables the project to benefit from the scalability, reliability, and management features provided by GCP.


### Learning Purposes and Deployment Choice:

**Kubernetes for Learning:** While the deployment on Kubernetes is not strictly necessary in that case, it is done primarily for learning purposes. Kubernetes offers valuable insights into container orchestration, scaling, and management, which are beneficial for developers aiming to enhance their skill set.

**Alternative Deployment Options:** For production deployments, a simpler approach such as Docker Compose might suffice, as it provides the necessary functionality to run the project in a containerized environment. Kubernetes, with its complexities, is typically chosen for projects requiring high scalability, redundancy, and advanced management features.


### Future Directions

While the current SRGAN model demonstrates promising results, several avenues for improvement and exploration can be considered:

**Extended Training Duration:** Given the resource constraints, the model could potentially benefit from longer training periods. Extending the training duration would likely lead to further refinement and improved performance.

**Larger and Diverse Dataset:** A more extensive and diverse dataset could contribute to enhancing the model's generalization capabilities and image quality.

**Enhanced Computational Resources:** Utilizing more powerful GPUs or distributed training could accelerate the training process and unlock greater model potential.

**Advanced Architectures:** Exploring newer and more complex architectures could yield additional performance gains, pushing the boundaries of image enhancement further.


In essence, the SRGAN project serves as a testament to the continuous pursuit of excellence in image enhancement, with the understanding that the journey doesn't end here. As technology advances and resources become more available, the potential for even more impressive results remains on the horizon.

## Tools Used

- Python
- Python libraries (Numpy, Pandas, Scikit-learn, OpenCV, Pillow, TensorFlow, Keras, Flask)
- Jupyter notebook, Visual Studio Code
- Javascript, React, HTML, CSS
- Docker
- Kubernetes
- Google Cloud

## Running the Application

Make sure You have installed Git and Docker.
To run the application locally, follow these steps:
```sh
git clone https://github.com/pmajews/image-quality-enhancement.git
```
Go to the cloned directory in command line and run this command:
```sh
docker-compose up
```
Click that link if upper commands were executed successfully: [http://localhost:5173/](http://localhost:5173/)