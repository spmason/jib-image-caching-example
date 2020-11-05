The `jib:dockerBuild` maven command doesn't utilise any caching when deciding what to upload to the docker daemon

This means that big image layer (eg lots of dependencies) can take a long time as they push a lot of redundant / duplicate data to docker

Simply download this repo and run `mvn clean compile jib:dockerBuild -X | grep TIMED`. A second run will show that the `Building image to Docker daemon` step takes just as long as the first time, though the actual images pushed (in `target/jib-cache/layers` are exactly the same