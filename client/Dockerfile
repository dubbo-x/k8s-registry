# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM golang:1.15-alpine AS base
WORKDIR $GOPATH/github.com/dubbo-x/k8s-registry/client
ADD . $GOPATH/github.com/dubbo-x/k8s-registry/client
ENV GOPROXY=https://goproxy.cn,direct
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -installsuffix cgo -o /client/client cmd/client.go

FROM alpine
COPY --from=base /client/client /client/client
COPY conf/client.yml conf/log.yml /client/
ENV CONF_CONSUMER_FILE_PATH "/client/client.yml"
ENV APP_LOG_CONF_FILE "/client/log.yml"
ENTRYPOINT ["/client/client"]