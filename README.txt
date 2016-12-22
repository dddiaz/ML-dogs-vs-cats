Setup:
1 - Build keras docker image
    docker build -t floydhub/dl-docker:cpu -f Dockerfile.cpu .

2 - start
    docker run -it -p 8888:8888 -p 6006:6006 -v /Users/danieldiaz/github/ML-dogs-vs-cats/sharedfolder:/root/sharedfolder floydhub/dl-docker:cpu jupyter notebook

    note:
    This shares the folder /sharedfolder on your host machine to /root/sharedfolder/ inside your container. 
    Any data written to this folder by the container will be persistent. 
    You can modify this to anything of the format -v /local/shared/folder:/shared/folder/in/container/. 

    also changed start from bash to jupyter notebook, change back if kernal not starting right

    http://127.0.0.1:8888 -> for notebook

3 - looks like cv2 is missin, need to install that
    added these to the docker file fyi
    pip install opencv-python
    pip install bcolz

    ran into a bunch of issues. make sure u use updated docker file

4 Updated Keras JSON - might not be neces
~/.keras/keras.json
"image_dim_ordering": "th",