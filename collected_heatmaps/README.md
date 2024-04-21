# Collected Heatmaps

- All collected heatmap images can be found at the [Webcam Google Drive/Collected Heatmaps Folder](https://drive.google.com/drive/folders/1dhmWjY4lw0inLqQ9HmOSrkijvOKNjWWI?usp=drive_link).
- If you do not have access to the folder, please send an email at `techandy42@gmail.com` or `dominique.brunet@ec.gc.ca` to gain access.

### About

- `overlay_heatmap_images.zip` contains each NavCan images overlayed with the Grad-CAM heatmaps.
- `cropped_heatmap_images.zip` contains each NavCan images cropped with only areas focused on Grad-CAM heatmaps.
- `overlay_agg_heatmap_images_threshold_50.zip` contains aggregated heatmaps for 7 NavCan cameras for each precipitation types, with lower threshold to include aggregated heatmaps areas.
- `overlay_agg_heatmap_images_threshold_70.zip` contains aggregated heatmaps for 7 NavCan cameras for each precipitation types, with higher threshold to include aggregated heatmaps areas.

### Observations

- The aggregated heatmaps contains too much noise to be useful (the variation of heatmaps within a class is greater than variation between classes), thus to observe the characteristics of the heatmaps, I recommend checking out images of webcams where the horizon of the image is located at least 30% above the bottom.
