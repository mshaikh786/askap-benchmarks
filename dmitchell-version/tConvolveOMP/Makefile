# Copyright (c) 2007 CSIRO
# Australia Telescope National Facility (ATNF)
# Commonwealth Scientific and Industrial Research Organisation (CSIRO)
# PO Box 76, Epping NSW 1710, Australia
# atnf-enquiries@csiro.au
#
# This file is part of the ASKAP software distribution.
#
# The ASKAP software distribution is free software: you can redistribute it
# and/or modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of the License,
# or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA
#

CXX=CC
CFLAGS=-O3 -fstrict-aliasing -fcx-limited-range -Wall -Wextra -fopenmp
DEBUG=-g
LDFLAGS=-dynamic -L/group/pawsey0001/mshaikh/software/cle60up05/forge-libs/18.0.2/GNU/4.9.3 -lmap-sampler-pmpi -lmap-sampler -Wl,--eh-frame-hdr -Wl,-rpath=/group/pawsey0001/mshaikh/software/cle60up05/forge-libs/18.0.2/GNU/4.9.3 
all:		tConvolveOMP

profile: 	tConvolveOMP-profile

		
Stopwatch.o:	Stopwatch.cc Stopwatch.h
		$(CXX) $(CFLAGS) -c Stopwatch.cc

Stopwatch-profile.o:	Stopwatch.cc Stopwatch.h
		$(CXX) $(CFLAGS) $(DEBUG) -c Stopwatch.cc

tConvolveOMP:	tConvolveOMP.cc Stopwatch.o
		$(CXX) $(CFLAGS) -c tConvolveOMP.cc
		$(CXX) $(CFLAGS) -o tConvolveOMP tConvolveOMP.o Stopwatch.o

tConvolveOMP-profile:	tConvolveOMP.cc Stopwatch-profile.o
		$(CXX) $(CFLAGS) $(DEBUG) -c tConvolveOMP.cc
		$(CXX) $(CFLAGS) $(DEBUG) -o tConvolveOMP-profile tConvolveOMP.o Stopwatch.o $(LDFLAGS)
clean:
		rm -f *.o tConvolveOMP tConvolveOMP-profile
