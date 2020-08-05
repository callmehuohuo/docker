FROM centos

MAINTAINER huohuo<345629829@qq.com>

ENV MYPATH /data/docker
WORKDIR $MYPATH

RUN yum -y install vim 
RUN yum -y install net-tools

EXPOSE 80

CMD echo $MYPATH
CMD echo "------构建完毕----"
CMD /bin/bash



