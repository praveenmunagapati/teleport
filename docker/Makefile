#
# Default target starts two Teleport clusters
#
.PHONY: up
up:
	docker-compose up

.PHONY: reup
reup:
	cd .. && make
	docker-compose up

# 'make down' stops all Teleport containers, deletes them
# and their network
#
.PHONY:down
down:
	docker-compose down

# `make enter-one` gives you shell inside auth server 
# of cluster "one"
#
.PHONY:enter-one
enter-one:
	docker exec -ti one /bin/bash

# `make enter-two` gives you shell inside auth server 
# of cluster "two"
#
.PHONY:enter-two
enter-two:
	docker exec -ti two-auth /bin/bash

# `make enter-two-proxy` gives you shell inside proxy server
# of cluster "two"
#
.PHONY:enter-two-proxy
enter-two-proxy:
	docker exec -ti two-proxy /bin/bash

# `make enter-two-node` gives you shell inside a node
# of cluster "two"
#
.PHONY:enter-two-node
enter-two-node:
	docker exec -ti two-node /bin/bash

.PHONY: setup-tc
setup-tc:
	docker exec -i two-auth /bin/bash -c "tctl -c /root/go/src/github.com/gravitational/teleport/docker/two-auth.yaml create -f /root/go/src/github.com/gravitational/teleport/docker/two-tc.yaml"

.PHONY: delete-tc
delete-tc:
	docker exec -i two-auth /bin/bash -c "tctl -c /root/go/src/github.com/gravitational/teleport/docker/two-auth.yaml rm tc/one"
