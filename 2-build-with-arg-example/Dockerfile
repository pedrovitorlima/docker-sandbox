FROM debian
LABEL mantainer 'Pedro Rodrigues'

#this argument can be setted by command line
#here we are configuring this with a default value 'files'
ARG S3_BUCKET=files 
#here we are setting a environment variable S3_BUCKET with the S3_BUCKET value
ENV S3_BUCKET=${S3_BUCKET}
#so, lets build the image without S3_BUCKET value
#>> docker image build -t ex-build-arg .
#>>docker container run ex-build-arg bash -c 'echo $S3_BUCKET' to print the var with default value
#the 'file' value will be showed because we dont build the image saying his value

#now lets build the image again with S3_BUCKET with 'myapp' value
#>>docker image build --build-arg S3_BUCKET=myapp . -t ex-build-arg .
#and execute this container asking debian to show this variable
#>>docker container run ex-build-arg bash -c 'echo $S3_BUCKET'