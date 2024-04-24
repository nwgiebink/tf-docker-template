FROM tensorflow/tensorflow:latest-gpu

ENV TZ=America/Los_Angeles
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip

RUN pip install \
    geopandas \
    rasterio 

CMD /bin/bash