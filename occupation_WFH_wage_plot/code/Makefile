#Definitions
FOLDERS = ../input ../output
#Recipes
all: ../output/occupation_WFH_wage_plot.eps

$(FOLDERS):
	mkdir $@
#Inputs recipes
../input/onet_teleworkable_blscodes.dta: ../../onet_to_BLS_crosswalk/output/onet_teleworkable_blscodes.dta  | ../input
	ln -s ../../onet_to_BLS_crosswalk/output/onet_teleworkable_blscodes.dta ../input/onet_teleworkable_blscodes.dta
../input/national_M2018_dl.xlsx: | ../input
	if [ -e ../../downloaddata/output/$(@F) ] ; then ln -s ../../downloaddata/output/$(@F) $@ ; else exit 1; fi
../output/occupation_WFH_wage_plot.eps: plot.do ../input/national_M2018_dl.xlsx ../input/onet_teleworkable_blscodes.dta | ../output
	stata-se -e $<
