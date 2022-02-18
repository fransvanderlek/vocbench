FROM adoptopenjdk/openjdk8:alpine

ENV vb_version=10.2.1
ENV st_version=10.2.1

ARG VB_TMP_FILE=vb_tmp.zip

#RUN cd /tmp
#RUN wget https://bitbucket.org/art-uniroma2/vocbench3/downloads/vocbench3-${vb_version}-full.zip
#COPY vocbench3-${vb_version}-full.zip /tmp
RUN set -eux ; \
	mkdir /opt/vocbench3 ; \
	mkdir /opt/vocbench3/data ; \
	cd /opt/vocbench3 ; \
	wget https://bitbucket.org/art-uniroma2/vocbench3/downloads/vocbench3-${vb_version}-full.zip; \
	unzip vocbench3-${vb_version}-full.zip ; \
	chmod -R u=rwX,go=rX semanticturkey-${st_version} ; \
	chmod +x semanticturkey-${st_version}/bin/* ; \
	sed -i 's/\(data\.dir\)=.*/\1=..\/data\/SemanticTurkeyData/' /opt/vocbench3/semanticturkey-${st_version}/etc/it.uniroma2.art.semanticturkey.cfg ; \
	rm vocbench3-${vb_version}-full.zip

WORKDIR /opt/vocbench3/semanticturkey-${st_version}

EXPOSE 1979

ENTRYPOINT ["bin/karaf"]
CMD ["server"]