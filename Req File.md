**Environment Setup for the Hybrid Quantum–Classical Framework**



This section defines the environment specifications required to reproduce the Hybrid Quantum–Classical (HQC) experiments. The implementation targets GPU-accelerated quantum simulation and high-dimensional 3D medical imaging workflows.



**System Requirements**



&nbsp;Python: Version 3.11 or higher

&nbsp;CUDA: Version 12.x (validated with CUDA 12.1 and 12.4)

&nbsp;Compute: NVIDIA GPU with CUDA and cuQuantum support





**Environment Configuration**



&nbsp;Deep Learning Framework: PyTorch

&nbsp;Quantum Machine Learning Framework: PennyLane

&nbsp;CUDA Dependency: Required for `custatevec-cu12` and `lightning.gpu` backend





**Dependency Specification (`requirements.txt`)**



  **Core Deep Learning and Numerical Computing** 

torch>=2.4.0

torchvision>=0.19.0

monai>=1.3.0

numpy>=1.26.0

pandas>=2.1.0



  **Quantum Machine Learning** 

pennylane>=0.36.0

pennylane-lightning>=0.36.0

pennylane-lightning-gpu>=0.36.0

custatevec-cu12



  **3D Medical Image Processing** 

SimpleITK>=2.3.1

scipy>=1.11.0

scikit-image>=0.22.0

opencv-python>=4.8.0



  **Classical Machine Learning Baselines** 

scikit-learn>=1.3.0

xgboost>=2.0.0

lightgbm>=4.1.0

catboost>=1.2.0



  **Generative Models, Utilities, and Analysis** 

tqdm

matplotlib

seaborn

shap>=0.44.0





**GPU Acceleration Configuration (CUDA 12)**



To enable the `lightning.gpu` backend with support for the Parameter-Shift Rule, ensure the following steps are completed.



&nbsp;**Step 1**: Install cuQuantum Components



&nbsp;		pip install custatevec-cu12



&nbsp;**Step 2**: Configure Environment Variables



Set the cuQuantum SDK path so it can be discovered by PennyLane:



&nbsp;		export CUQUANTUM\_SDK=$(python -c "import site; print(f'{site.getsitepackages()\[0]}/cuquantum')")

&nbsp;		export LD\_LIBRARY\_PATH=$CUQUANTUM\_SDK/lib:$LD\_LIBRARY\_PATH





 **Step 3**: Verify GPU Quantum Device



&nbsp;		import pennylane as qml

&nbsp;		Successful initialization confirms correct CUDA and cuQuantum setup

&nbsp;		dev = qml.device("lightning.gpu", wires=16)





 **Key Architecture Components**



&nbsp;3D Swin Transformer: Utilized via `torchvision.models.video.swin3d\_t` for volumetric feature extraction

&nbsp;Focal Loss: Implemented either custom or through `torchvision.ops.sigmoid\_focal\_loss`

&nbsp;WGAN-GP: Includes explicit gradient penalty computation for 3D discriminator stability

