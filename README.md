# Decoupled Multimodal Distilling for Emotion Recognition, CVPR 2023

Human multimodal emotion recognition (MER) aims to perceive human emotions via language, visual and acoustic modalities. Despite the impressive performance of previous MER approaches, the inherent multimodal heterogeneities still haunt and the contribution of different modalities varies significantly. We propose a decoupled multimodal distillation (DMD) approach that facilitates flexible and adaptive crossmodal knowledge distillation. Specially, the representation of each modality is decoupled into two parts, i.e., modality-irrelevant/-exclusive spaces. DMD utilizes a graph distillation unit (GD-Unit) for each decoupled part so that each GD can be performed in a more specialized and effective manner. A GD-Unit consists of a dynamic graph where each vertice represents a modality and each edge indicates a dynamic knowledge distillation. Such GD paradigm provides a flexible knowledge transfer manner where the distillation weights can be automatically learned, thus enabling diverse crossmodal knowledge transfer patterns.

<img src="figure_1.png" width="50%"></img>

Motivation and main idea: (a) illustrates the significant emotion recognition discrepancies using unimodality, adapted from [Mult](https://github.com/yaohungt/Multimodal-Transformer). (b) shows the conventional cross-modal distillation. (c) shows our proposed DMD.

![](figure2.png)
The framework of DMD. Given the input multimodal data, DMD encodes their respective shallow features $\widetilde{\mathbf{X}}\_{m}$, where $m \in \{L, V, A\}$. In feature decoupling, DMD exploits the decoupled homo-/heterogeneous multimodal features $\mathbf{X}^{\text{com}}\_{m}$ / $\mathbf{X}^{\text{prt}}\_{m}$ via the shared and exclusive encoders, respectively. $\mathbf{X}^{\text{prt}}\_{m}$ will be reconstructed in a self-regression manner. Subsequently, $\mathbf{X}^{\text{com}}\_{m}$ will be fed into a GD-Unit for adaptive knowledge distillation in HomoGD. In HeteroGD, $\mathbf{X}^{\text{prt}}\_{m}$ are reinforced to $\mathbf{Z}^{\text{prt}}\_{\to m}$ via multimodal transformers to bridge the distribution gap. The GD-Unit in HeteroGD takes $\mathbf{Z}^{\text{prt}}\_{\to m}$ as input for distillation. Finally, $\mathbf{X}^{\text{com}}\_{m}$ and $\mathbf{Z}^{\text{prt}}\_{\to m}$ will be adaptively fused for MER. 

![](edge.png)
Illustration of the graph edges in HomoGD and HeteroGD. In (a), $L \to A$ and $L \to V$ are dominated because the homogeneous language features contribute most and the other modalities perform poorly. In (b), $L \to A$, $L \to V$, and $V \to A$ are dominated.  $V \to A$ emerges because the visual modality enhanced its feature discriminability via the multimodal transformer mechanism in HeteroGD.

