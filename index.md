# DSC 180A Methodology Assignment 4

**Name:** Andrew Youn
**Email:** [asyoun@ucsd.edu](mailto:asyoun@ucsd.edu)
**Section:** D32 Steering Diffusion Models
**Mentor:** Yusu Wang

---

**1. What is the most interesting topic covered in your domain this quarter?**

Flow matching is the most interesting topic that we've covered in my domain this quarter because it's basically the same thing as the diffusion we've already learned. If you train a denoiser to guess the clean data point and turn that guess into a velocity, then flow matching on a straigh noise to data path is exactly diffusion with the DDIM sampler. 

**2. Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

When during sampling does steering actually matter? In my checkpoint I found that CFG on CIFAR-10 pushed class accuracy from about 12% (no guidance) to about 99% but FID got worse as the guidance strength went up. Since the model learns the high-noise part first and the fine details last, I'd like to test turning guidance on only for part of the sampling process or using a guidance strength that changes over time and see if that keeps the accuracy gain while losing less image quality.

**3. What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

I would definitely like to make the evaluation more solid. Right now our comparisons use about 1,000 images per setting, which makes small FID differences hard to trust so I'd use more samples and repeat runs with different seeds to get error bars. I'd also add metrics that separate quality from variety like precision and recall since FID mixes the two and guidance mostly trades one for the other.

**4. What other techniques would you be interested in using in your project?**

At the moment im not sure but there are a couple of things I've been looking into. For example, I have heard about reward-based steering where a separate scoring model nudges samples during sampling or fine tuning the model toward a reward which could be interesting to implement. Something else I could possible try is using few step samplers and distillation to see how steering behaves when we only get a handful of sampling steps.
