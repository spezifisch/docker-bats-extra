# This file is part of docker-bats-extra (https://github.com/spezifisch/docker-bats-extra).
# Copyright (c) 2022 spezifisch (https://github.com/spezifisch)
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, version 3 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM bats/bats:1.5.0

# add libraries: https://bats-core.readthedocs.io/en/stable/writing-tests.html#libraries-and-add-ons

# https://github.com/bats-core/bats-support
ARG BATS_SUPPORT_COMMIT_ID=d140a65044b2d6810381935ae7f0c94c7023c8c3
ARG BATS_SUPPORT_ZIP_SHA256=d213d17577ba32cb4c0e0a169e4cb029dd20bcba15cb079b1d5021512344fc5d

# https://github.com/bats-core/bats-assert
ARG BATS_ASSERT_COMMIT_ID=4bdd58d3fbcdce3209033d44d884e87add1d8405
ARG BATS_ASSERT_ZIP_SHA256=a80443a1734cdc50687df642fb23157252b1192708610de9cb095310c126cdb7

# https://github.com/bats-core/bats-file
ARG BATS_FILE_COMMIT_ID=17fa557f6fe28a327933e3fa32efef1d211caa5a
ARG BATS_FILE_ZIP_SHA256=31095cf329efe774d41fe45790cd32f01cbbe69e54ea25baa3bc7e258dfc0992

ARG TEST_HELPER=/test_helper
ENV TEST_HELPER=$TEST_HELPER

# for the pipes inside the RUN below
SHELL ["/usr/local/bin/bash", "-o", "pipefail", "-c"]

WORKDIR $TEST_HELPER
# hadolint ignore=DL4006
RUN wget "https://github.com/bats-core/bats-support/archive/${BATS_SUPPORT_COMMIT_ID}.zip" -qO bats-support.zip \
    && [ "${BATS_SUPPORT_ZIP_SHA256}" = "$(sha256sum bats-support.zip | cut -d' ' -f1)" ] \
    && unzip bats-support.zip \
    && rm bats-support.zip \
    && mv "bats-support-${BATS_SUPPORT_COMMIT_ID}" bats-support \
    && wget "https://github.com/bats-core/bats-assert/archive/${BATS_ASSERT_COMMIT_ID}.zip" -qO bats-assert.zip \
    && [ "${BATS_ASSERT_ZIP_SHA256}" = "$(sha256sum bats-assert.zip | cut -d' ' -f1)" ] \
    && unzip bats-assert.zip \
    && rm bats-assert.zip \
    && mv "bats-assert-${BATS_ASSERT_COMMIT_ID}" bats-assert \
    && wget "https://github.com/bats-core/bats-file/archive/${BATS_FILE_COMMIT_ID}.zip" -qO bats-file.zip \
    && [ "${BATS_FILE_ZIP_SHA256}" = "$(sha256sum bats-file.zip | cut -d' ' -f1)" ] \
    && unzip bats-file.zip \
    && rm bats-file.zip \
    && mv "bats-file-${BATS_FILE_COMMIT_ID}" bats-file

WORKDIR /code
