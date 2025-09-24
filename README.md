<img width="1512" height="982" alt="スクリーンショット 2025-09-24 午後9 16 47" src="https://github.com/user-attachments/assets/00cdaa0c-e0bf-4167-aaef-6f43ac6206cc" />

This cel-shading post-processing effect is based on a couple of YouTube tutorials by Evans Bohl (https://www.youtube.com/@evansbohl), with my own modifications and refactoring. Luminance is posterized into two levels, while I've opted for more with the base color. Currently, there's a discoloration issue that needs to be addressed, but I'm otherwise happy with the overall appearance.
Depth outlines use the same convolution kernel as in tutorials, namely

$$
\begin{pmatrix}
0 & -1 & 0\\
-1 & 4 & -1\\
0 & -1 & 0
\end{pmatrix}
$$

as I didn't notice a marked improvement when using other kernels (and this one is simpler to implement in Unreal's material graph). I also opt for using the dot product between normals (instead of distance), though they're essentially equivalent due to working with unit vectors; it's simply a matter of preference, since I think the dot product more closely represents the idea behind what we're doing (judging whether the normals are similar or not).
