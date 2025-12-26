# spurious-correlations-mllms

Please look at the slides! - Group15.pdf

High-Level Ideas:
- Make image-image alignment equivalent to image-text alignment. Also equivalent to text-text alignment.
- image-image alignment ~ image-text alignment with gradcam matching rank loss
- text-text alignment with reasoning distillation from MLLMs (which layer do we manipulate alignment 1024 layer/FFN layer in transformer architecture? (most probably not the attention layer ofc))
- Not sure how to measure text-text alignment as such or how to compare with image-image or image-text.

My og thought process: https://docs.google.com/document/d/15WJied-S7sh3CfDdIAicxEbdJ09xj9rRBYvK6-Ds9Lo/edit?tab=t.0
Results disorganized: https://docs.google.com/spreadsheets/d/1jWxUiCW3SAt7AEAttzhLwMEjERnz6ITQrs68aegMw-k/edit?gid=292252817#gid=292252817

Experiments:
- Setting: 2000 samples training out of 4795 waterbirds
- cat vs not cat experiment CLIP TE (TE cannot differentiate well between the reps)
- gradcam to show how our method is doing
- replace stable diffusion with our CLIP TE (to be done)
- measure text generation capability after our training to ensure that hasn'e been lost (to be done)

Technical Notes for now:
- train_clip.py file you should ignore for our training setup. This is cause same text we duplicate in that but same text can't be a positive and negative in contrastive learning. Can use train_clip_binary for waterbirds and celebA
- train_clip_align_simultaneously worked the best iirc. And within that training mode text_image_concat_no_bg cause that's what's doing full alignment ig.
- train_clip_align_separately expected it to work well but didn't iirc
