
# Wheat_Count_Update_ZH


#### Labeling tool update [(Code)](https://github.com/px39n/LabelWheat_points):

- Point labeling--->Line labeling
- Add reference segementation image (using Custom Threshold Binarization)
<img src="https://github.com/px39n/LabelWheat_points/blob/master/op.gif?raw=true" height="200"/>



#### Dataset
- Create labeled Wheat_multi_scale dataset(WMSD) including 33 images for current.
- Diversity includes spatial resolution(D), Plant growth stage, Camera View

Table: WMSD overall according to scale
<table border="0" class="ke-zeroborder">
	<tbody>
		<tr>
			<td colspan="2">
				<div>
					camera view
				</div>
			</td>
			<td colspan="3">
				wheat growth stage
			</td>
		</tr>
		<tr>
			<td colspan="2">
				ortho(P)
			</td>
			<td>
				heading(G)
			</td>
			<td>
				flowering(H)
			</td>
			<td>
				mature(M)
			</td>
		</tr>
		<tr>
			<td rowspan="3">
				spatial resolution
			</td>
			<td>
				low(L)
			</td>
			<td>
				0
			</td>
			<td>
				0
			</td>
			<td>
				0
			</td>
		</tr>
		<tr>
			<td>
				medium(M)
			</td>
			<td>
				12
			</td>
			<td>
				&nbsp;
			</td>
			<td>
				1
			</td>
		</tr>
		<tr>
			<td>
				high(H)
			</td>
			<td>
				5
			</td>
			<td>
				5
			</td>
			<td>
				5
			</td>
		</tr>
		<tr>
			<td colspan="2">
				tilt(V)
			</td>
			<td>
				heading(G)
			</td>
			<td>
				flowering(H)
			</td>
			<td>
				mature(M)
			</td>
		</tr>
		<tr>
			<td rowspan="3">
				spatial resolution
			</td>
			<td>
				low(L)
			</td>
			<td>
				&nbsp;
			</td>
			<td>
				&nbsp;
			</td>
			<td>
				&nbsp;
			</td>
		</tr>
		<tr>
			<td>
				medium(M)
			</td>
			<td>
				1
			</td>
			<td>
				&nbsp;
			</td>
			<td>
				&nbsp;
			</td>
		</tr>
		<tr>
			<td>
				high(H)
			</td>
			<td>
				5(1)
			</td>
			<td>
				5
			</td>
			<td>
				5(1)
			</td>
		</tr>
	</tbody>
</table>




#### Model: 
[model on Google Colab](https://colab.research.google.com/drive/1oIx7ymw9D52MdqMrzggfn4LmIG3OQyeg#scrollTo=-f-jjZBKqIes)
- Propose a adaptive line density map algorithm based on adaptive Gaussian kernel
(Point Gaussian kernel sequence according to the length)


<img src="https://github.com/px39n/Wheat-Counting-Update/blob/master/train_sample.JPG?raw=true" height="200"/>

- Evaluated two network MCNN and RSNet and compare thier accuracy on WMSD

Network | ovall-MAE | overall-MSE| Precision | MAE/MSE/P in XX scale
---|--- |---|---|---
MCNN | 8.73  | 12.38 |  | 
CRSNet | 4.41 | 6.27 | | 
Normal CNN |   |  |  | 



#### The latest wheat detection


-  The Global Wheat Detection Competition([kaggle](https://www.kaggle.com/c/global-wheat-detection/overview)) produced a large number of excellent wheat recognition algorithms 
- 3392 labeled wheat images open access to the public
- Different growth stages were considered but the scale is fixed(land-based)
#### Future Works:


- The detection methods in competition can be used to quickly label UAV images.

- Use structural similarity index measure) SSIMs instead of L2 to measure the structure similarity

-  Add more images to adjust network
