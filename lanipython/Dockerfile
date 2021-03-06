# Copyright 2020 Chi-kwan Chan
# Copyright 2020 Steward Observatory
#
# Licensed under the Apache License, Version 2.0 (the "License"); you
# may not use this file except in compliance with the License.  You
# may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
# implied.  See the License for the specific language governing
# permissions and limitations under the License.

ARG	dsttag=3.8.6,20201215,3.8,3,latest
ARG	srctag=20201117
ARG	digest=sha256:83323df595e261d5aabf0c96c5ae65dcaa42049495c86de21f54c39d61a824ff

#==============================================================================
# The base image: an official python image

FROM	python@${digest} AS base
LABEL	maintainer="Chi-kwan Chan <chanc@arizona.edu>"

RUN     sed -i- 's/^#//g;s/^d/# d/g;s/^ //g;' /etc/apt/sources.list &&\
	echo 'Acquire::Check-Valid-Until false;' > /etc/apt/apt.conf.d/10nochk

#==============================================================================
# The builder image: the Laniakea base image

FROM	l6acon/lanibase:${srctag} AS builder

#==============================================================================
# The Laniakea python runtime image

FROM	base
ENV	LANG=C.UTF-8 \
	LC_ALL=C.UTF-8

COPY	--from=builder /usr/local/sbin/* /usr/local/sbin/
RUN	chmod u+s /usr/local/sbin/selfadd

ENTRYPOINT	["/usr/local/sbin/entrypoint"]
CMD	["python3"]
