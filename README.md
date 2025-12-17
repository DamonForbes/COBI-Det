# COBI-Det Dataset
The official dataset links for the paper "From Rubbings to Reality: A High-Fidelity RGB Benchmark and Lightweight Transformer for Oracle Bone Inscriptions Detection". The dataset will be made public shortly after the acceptance of the paper.

## Dataset Introduction
The COBI-Det dataset is a high-resolution RGB dataset designed to simulate real-world archaeological scenarios for Oracle Bone Inscriptions (OBIs) detection. Existing public datasets for OBIs detection predominantly consist of grayscale rubbing images. While these benchmarks have facilitated early research, they represent an idealized data form that lacks the complex environmental noise, material aging, and chromatic interference found in real-world archaeological excavations. Consequently, models trained solely on grayscale rubbings often struggle to generalize to authentic fragments rich in textural and color information.

## Data Acquisition and Annotation
The dataset consists of authentic Oracle Bone fragments sourced from the Anyang Huanbaozhai Oracle Bone Culture Museum. High-resolution images were acquired using a SONY digital camera to ensure fine-grained capture of textural details. To ensure ground-truth reliability, all fragments were authenticated by paleographic experts. We utilized LabelImg for meticulous character-level annotation, which was subsequently rigorously verified by domain specialists.

## Degradation Characteristics
Unlike conventional datasets, our dataset explicitly preserves surface degradation patterns inherent to unearthed artifacts. Drawing upon the classification standards outlined in [26], the dataset encapsulates five distinct types of degradation:
- Surface Exfoliation: Manifests as sheet-like separation or surface detachment caused by aging adhesives or bone structure deterioration.
- Color Infiltration: Refers to surface discoloration caused by environmental substances (e.g., bronze corrosion, blood, pigments) penetrating bone pores.
- Biological Residues: Involves metabolic waste deposits from insects or other organisms on the bone surface.
- Foreign Adhesion: Includes extraneous materials like cotton fibers, sand, or residual wax attached during historical preservation.
- Adhesive Stains: Residual glues from past maintenance, resulting in unnatural gloss or grime accumulation.

## Stratified Splitting and Augmentation Strategy
To guarantee a robust evaluation and strictly prevent data leakage, we employed a stratified split-then-augment strategy. The original dataset was first partitioned into training, validation, and testing sets following a 7:1:2 ratio. Crucially, data augmentation was applied exclusively to the training subset after the split. As shown in Fig. 3, we implemented offline augmentation techniques—including random rotation, spatial shifting, illumination adjustment, and noise injection—to simulate diverse capture conditions and expand the training distribution. This process expanded the training set to 1,065 images while keeping the validation and test sets purely authentic to ensure fair performance evaluation.

## Dataset Statistics
The final processed dataset comprises a total of 1,158 images containing 5,573 annotated instances, with an average of 4.81 targets per image. The specific distribution is detailed as follows:
1. Training Set: Contains 1,065 images with 5,110 instances. The dense augmentation ensures broad coverage of geometric and photometric variations.
2. Validation Set: Contains 33 original images with 183 instances. This subset features a high target density (mean: 5.55 instances/image) and a wide range of targets (1–42 per image), serving as a challenging proxy for model selection.
3. Test Set: Contains 60 original images with 280 instances. With a density range of 1–12 instances per image, this set is used for the final unbiased evaluation of the model’s generalization capability.
