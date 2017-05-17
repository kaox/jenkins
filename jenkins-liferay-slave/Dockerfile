FROM kaox/jenkins-slave

#ANT
ENV ANT_VERSION=1.9.9
ENV ANT_HOME=/opt/ant

# change to tmp folder
WORKDIR /tmp

# Download and extract apache ant to opt folder
RUN wget --no-check-certificate --no-cookies http://archive.apache.org/dist/ant/binaries/apache-ant-${ANT_VERSION}-bin.tar.gz \
    && wget --no-check-certificate --no-cookies http://archive.apache.org/dist/ant/binaries/apache-ant-${ANT_VERSION}-bin.tar.gz.md5 \
    && echo "$(cat apache-ant-${ANT_VERSION}-bin.tar.gz.md5) apache-ant-${ANT_VERSION}-bin.tar.gz" | md5sum -c \
    && tar -zvxf apache-ant-${ANT_VERSION}-bin.tar.gz -C /opt/ \
    && ln -s /opt/apache-ant-${ANT_VERSION} /opt/ant \
    && rm -f apache-ant-${ANT_VERSION}-bin.tar.gz \
    && rm -f apache-ant-${ANT_VERSION}-bin.tar.gz.md5
COPY conf/ecj.jar /opt/ant/lib

# add executables to path
RUN update-alternatives --install "/usr/bin/ant" "ant" "/opt/ant/bin/ant" 1 && \
    update-alternatives --set "ant" "/opt/ant/bin/ant"

# SDK Liferay
COPY liferay-plugins-sdk-6.2-ee-sp14-20151105114451508.tar.gz /tmp
COPY bundles.tar.gz /tmp
RUN tar -zvxf liferay-plugins-sdk-6.2-ee-sp14-20151105114451508.tar.gz -C /home/jenkins/ && \
	tar -zvxf bundles.tar.gz -C /home/jenkins/ && \
	rm -f /tmp/bundles.tar.gz && \
	rm -f /tmp/liferay-plugins-sdk-6.2-ee-sp14-20151105114451508.tar.gz
COPY conf/ivy-settings.xml /home/jenkins/liferay-plugins-sdk-6.2-ee-sp14
COPY conf/build.properties /home/jenkins/liferay-plugins-sdk-6.2-ee-sp14
