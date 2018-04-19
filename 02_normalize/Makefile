DB=enceladus
BUILD=${CURDIR}/build.sql
SCRIPTS=${CURDIR}/scripts
CSV='${CURDIR}/data/master_plan.csv'
MASTER=$(scripts)/import.sql
NORMALIZE=$(scripts)/normalize.sql

all: normalize
  	psql $(DB) -f $(BUILD)

master:
	@cat $(MASTER) >> $(BUILD)

import: master
  	@echo  "COPY import.master_plan FROM
$(CSV) WITH DELIMITER ',' HEADER CSV;" >> $(BUILD)

normalize: import
  	@cat $(NORMALIZE) >> $(BUILD)

clean:
	@rm -rf $(BUILD)
