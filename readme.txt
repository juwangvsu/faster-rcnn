
-------------status: running traiining ok, 6/7 2pm---------------
check 
"to run"
tbd: 
	docker image pyenv two pytorch
	run 3d-vehicle-tracking with this faster-rcnn

------------6/7/2020 google colab example ------------------------
Shared from Choi:
	Test_faster-rcnn.ipynb
	Faster-rcnn.ipynb
	3d-vehicle-tracking.ipynb
My drive/Colab notebooks/
	Readme-3dtracking.ipynb
------------------------------------------------------------------
the fast-rcnn.pytorch included is "old" and compiled with torch 0.4

"new" fast-rcnn.pytorch at seperate folder build with torch 1.2.0 and require other packages. it build well with colab, see notepad test_faster-rcnn.ipynb

building locally at docker image
--- current status: build succ, after the following tweaks:
    --- pip install torch==1.5.0 pycocotools scipy==1.1.0 pillo==6.1
--- to build:
	google notepad test_faster-rcnn.ipynb, 

	or locally with docker image jwang3vsu/cuda90py3ub16
		docker info:
			1T ssd#6, dockerimg, /Documents/pose6d/cuda90py3/readme.txt
			 docker run --gpus all --rm -it -v "/media/student/data4/pose6d:/app" \
				 jwang3vsu/cuda90py3ub16:latest bash
	
	cd lib; python3 setup.py build develop
	to rebuild, cd lib; rm -rf build/*, then run setup.py above
--- google share/local repo:
	the repo is cloned at 
		My Driver/faster-rcnn
		@1T ssd#6, data4/pose6d/faster-rcnn
		a
--- to run:
	 python3 trainval_net.py \
                   --dataset pascal_voc --net vgg16 \
                   --bs 2 --nw 1 --epochs 6\
                   --lr 1e-2 --lr_decay_step 4 \
                   --cuda	
	nw >2 local machine run outof memory
git clone -b pytorch-1.0 https://github.com/jwyang/faster-rcnn.pytorch.git
