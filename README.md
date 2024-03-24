# SAE-and-Custom-Penalty-Function-for-KMNIST
Using an SAE, then SAE with Custom Penalty Function, to classify the KMNIST Dataset again.

## Part 1- Using SAE to classify KMNIST, then injecting noise
* Used an SAE, in which we pass the codes (output of the middle bottleneck layer) into a MLP classifier
* Comparing the MSE cost function to the Correntropy (CE) cost function in the noise scenario

## Part 2- Using SAE to classify KMNIST, using the cost function J_custom = L + lambda*R
* Used a custom loss function for the above SAE, where it's a linear combination of MSE and the Euclidean distance of the current codes to its constellation target (with the goal of minimizing their distance)- the constellation targets are targets we create BEFOREHAND, and place them as far away apart as possible (in space of codes), such that they'd be MAXIMALLY DISCRIMINITIVE!

* The below image I saw from a YT video shows this:

* ![image](https://github.com/Zain3/SAE-and-Custom-Penalty-Function-for-KMNIST/assets/70613917/0ea3a6f5-7578-44eb-b10d-6d90a98093c8)

* Where the modified SAE has 2 outputs that train the SAE in TWO DIFFERENT ways:
1. Overall output of model, trained using a regular MSE cost function, or L
2. Output of bottleneck layer, trained using the dstiance between the current code and it's constellation target, or R, multiplied by lambda

I made a visualation of a custom SAE architecture with multiple outputs in TensorFlow, which is shown here:
![image](https://github.com/Zain3/SAE-and-Custom-Penalty-Function-for-KMNIST/assets/70613917/57eebff6-aa48-4926-bad5-3af15607c25f)



