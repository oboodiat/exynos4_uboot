#
# (C) Copyright 2000-2003
# Wolfgang Denk, DENX Software Engineering, wd@denx.de.
#
# (C) Copyright 2008
# Guennadi Liakhovetki, DENX Software Engineering, <lg@denx.de>
#
# (C) Copyright 2011 Samsung Electronics Co. Ltd
#
# See file CREDITS for list of people who contributed to this
# project.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of
# the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA
#

include $(TOPDIR)/config.mk

LIB	= $(obj)lib$(SOC).o

#SOBJS	+= reset.o
COBJS	+= irom_copy.o
COBJS	+= nand.o
COBJS	+= nand_cp.o
ifdef CONFIG_CMD_NAND
COBJS	+= nand_write_bl.o
endif
COBJS	+= onenand_cp.o

ifdef CONFIG_HKDK4212
COBJS	+= pmic_hkdk4212.o
else
ifdef CONFIG_HKDKC210
COBJS	+= pmic_hkdk4210.o
else
ifndef CONFIG_EXYNOS4_GALAXY
COBJS	+= pmic.o
else
COBJS	+= i2c.o
COBJS	+= i2c_gpio.o
endif
endif
endif

ifdef CONFIG_SECURE_BOOT
COBJS	+= UBOOT_SB20_S5PC210S.o
COBJS	+= security_check.o
COBJS	+= ace_sha1.o
endif
COBJS	+= reset.o
COBJS	+= gpio.o
COBJS	+= movi_partition.o
COBJS	+= sys_info.o
COBJS	+= clock.o
COBJS	+= setup_hsmmc.o

SRCS	:= $(SOBJS:.o=.S) $(COBJS:.o=.c)
OBJS	:= $(addprefix $(obj),$(COBJS) $(SOBJS))

all:	 $(obj).depend $(LIB)

$(LIB):	$(OBJS)
	$(call cmd_link_o_target, $(OBJS))

#########################################################################

# defines $(obj).depend target
include $(SRCTREE)/rules.mk

sinclude $(obj).depend

#########################################################################
