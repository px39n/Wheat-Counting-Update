
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
[MCNN model on Google Colab](https://colab.research.google.com/drive/1oIx7ymw9D52MdqMrzggfn4LmIG3OQyeg#scrollTo=-f-jjZBKqIes)
[WDCN model on Google Colab](https://colab.research.google.com/drive/1XnuYC7Zja1QnJVx6fvbEmJjW0eCXLNhU?usp=sharing)
[Article on Google Doc](https://docs.google.com/document/d/19SvvBv9TvnBNH9PCDPEJwj_M22tNus4HlqSmUcLgriI/edit?usp=sharing)

- Propose a adaptive line density map algorithm based on adaptive Gaussian kernel
(Point Gaussian kernel sequence according to the length)


<img src="https://github.com/px39n/Wheat-Counting-Update/blob/master/train_sample.JPG?raw=true" height="200"/>

- Proposed a End to End Dilated network suitable for different scale scenes

- Evaluated two network MCNN and WDCN and compare thier accuracy on WMSD and spike

- Three images were used as pre-training due to average low value of WMSD line density map( easy to converge to 0)

Network | ovall-MAE | overall-MSE| SPIKE MAE | overall
---|--- |---|---|---
MCNN | 8.73  | 12.38 | 7.25 | 
Tasselnet | 9.7 | 13.8 | 5.96| 
WDCN |  4.41 |  6.27 | 2.83 | 



#### The latest wheat detection


-  The Global Wheat Detection Competition([kaggle](https://www.kaggle.com/c/global-wheat-detection/overview)) produced a large number of excellent wheat recognition algorithms 
- 3392 labeled wheat images open access to the public
- Different growth stages were considered but the scale is fixed(land-based)
#### Future Works:


- The detection methods in competition can be used to quickly label UAV images.

- Use structural similarity index measure) SSIMs instead of L2 to measure the structure similarity

-  Add more images to adjust network
