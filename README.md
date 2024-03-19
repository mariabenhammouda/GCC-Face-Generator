# GCC-Face-Generator
## Motivation

The face and its features represent the most intuitive and personal aspect of humans. Its uniqueness underscores the value of extracting features and information, termed soft biometrics, which greatly enhances recognition performance and refines search algorithms for facial images. While these advancements offer promising applications across various domains such as law enforcement, surveillance, advertising, and social media profiling, a critical gap emerged upon reviewing existing literature. More specifically, there is a notable absence of representation of the Arab world, and when present, it tends to be unfairly represented. Moreover, the current face generators available in the market fall short of accurately generating specific subgroups within the Arab population, such as Levantine, Gulf Cooperation Council (GCC), Egyptian, and North African individuals.

### To my knowledge, this is the first GAN-powered face image generator tailored to GCC representation.
Below are three images generated using different AI text-to-image face generators, highlighting evident misrepresentation. These images frequently depict stereotypes and Arab tropes, including black beards, head wraps, and stereotypical "Arabian" clothing:


![903a67ec-039d-456b-a35c-a060a1f94956](https://github.com/mariabenhammouda/GCC-Face-Generator/assets/102983688/614bf0c8-2596-4d3a-8808-ac3fcea0051e) ![44e77f76-5238-4b9d-a84a-0afde8ab1258](https://github.com/mariabenhammouda/GCC-Face-Generator/assets/102983688/3a41faca-13e9-40d6-946e-b4d4fa3f674f)

## Approach
The code creates a Generative Adversarial Network (GAN) architecture with TensorFlow and Keras. The GAN is made up of two models: the generator and the discriminator. The generator creates bogus pictures from random noise, but the discriminator distinguishes between actual and fake images. The generator network has layers, including Dense, LeakyReLU, Reshape, Conv2D, and Conv2D. The transpose layers convert the input noise into a realistic image. To categorize pictures as real or fake, the discriminator network uses Conv2D, LeakyReLU, Dropout, and Dense layers. In addition, the algorithm creates the GAN model by joining the generator and discriminator models. It makes the discriminator non-trainable during GAN training to prevent it from being updated when the generator is taught. The GAN model is compiled with an RMSprop optimizer and binary cross-entropy loss function for training.

## Results
Both discriminator and adversarial losses fluctuate over the training process.
The discriminator loss generally remains below 1.
The adversarial loss shows more variability, ranging from very low values to over 3.
The training time per step is relatively consistent, around 6.6 to 7.0 seconds.

![image](https://github.com/mariabenhammouda/GCC-Face-Generator/assets/102983688/d62d26e7-6c07-44f4-9b1d-e6730f2aad81)

I am experimenting with different activation functions and the number of layers to find a combination that pushes the discriminator loss to be a bit higher and reduces the generator loss to less than 1. Despite the large computational power and the long time it takes to train 15,000 epochs, I find this area very rewarding to work on, and I hope to perfect the model so that concurrent users can benefit from it.


Currently, the generated faces exhibit a cartoonish appearance and often appear blurry. Interestingly, when I asked participants from Arab regions to identify or guess the origin of these individuals, they consistently associated them with the Gulf region.


![Screen Shot 2024-03-19 at 12 54 07 PM](https://github.com/mariabenhammouda/GCC-Face-Generator/assets/102983688/27434cf8-fd62-4fcc-bf9b-dd32400845d9) ![Screen Shot 2024-03-19 at 12 55 29 PM](https://github.com/mariabenhammouda/GCC-Face-Generator/assets/102983688/0f066d0b-8dde-47f9-98ca-f64b770ec004) ![Screen Shot 2024-03-19 at 12 53 07 PM](https://github.com/mariabenhammouda/GCC-Face-Generator/assets/102983688/eb629c4e-4abf-4dbb-8b1e-83df84c0f618)

I would also like to give credit to this paper for creating the GCC training dataset: N. A. A. -H. And M. Prince, "A Classification of Arab Ethnicity Based on Face Image Using Deep Learning Approach," in IEEE Access, vol. 9, pp. 50755-50766, 2021, doi: 10.1109/ACCESS.2021.3069022.
