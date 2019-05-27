#!/bin/sh

# Copyright (c) 2019 Andrew Steel <copyright@andrewsteel.net>
#
# SPDX-License-Identifier: MIT-0
#
# The MIT No Attribution License:
#
# Permission is hereby granted, free of charge, to any person
# obtaining a copy of this software and associated documentation
# files (the "Software"), to deal in the Software without restriction,
# including without limitation the rights to use, copy, modify, merge,
# publish, distribute, sublicense, and/or sell copies of the Software,
# and to permit persons to whom the Software is furnished to do so.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT.
# IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
# CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
# TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
# SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

# Copy Names:
# Copies the names of selected files to the X clipboard selection, using either
# 'xsel' or 'xclip' (in that order) if available.

unset -v \
	names
IFS="$(printf '\n!')"; IFS="${IFS%!}"
for FILE_PATH in ${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS}; do
	names="${names:+${names}${IFS}}$(basename "${FILE_PATH}")"
done

printf '%s' "${names}" \
| {
	if test "$(command -pv xsel)"; then
		xsel -ib -l /dev/null
	elif test "$(command -pv xclip)"; then
		xclip -i -selection clipboard -f
	fi
}
