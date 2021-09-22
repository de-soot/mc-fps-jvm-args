# Read these first to customise the settings to suit your system :

"-d64" - Makes the Java application (in this case, it's Minecraft) run as a 64-bit program; only use this if your operating system is 64-bit, otherwise remove this parameter.

"-Xmx 2G -Xms 2G" - Allocates 2 GB of RAM to the Java application (in this case, it's Minecraft) at launch; you should always leave at least 1 GB (2 GB is recommended) for your system.

"-XX:ReservedCodeCacheSize=1024m" - Sets the cache size for reserved code that the Java application (in this case, it's Minecraft) might reuse. This should be half of the RAM allocated to Minecraft; in my case, I have allocated 2 GB (2048 MB) of RAM, so I will use 1024m (1 GB).

"-XX:SoftRefLRUPolicyMSPerMB=4000" - Tells the Java application (in this case, it's Minecraft) how much milliseconds to use per MB of soft references. If you only allocated 1 GB to Minecraft, use 2000 instead; but since I allocated 2 GB, I use 4000.

"-XX:ParallelGCThreads=4" - Tells the Java application (in this case, it's Minecraft) how many logical processors (threads) your CPU has; I have 4 threads so I set it to 4.

# The arguments (fitted to my system) :
-XX:+UnlockExperimentalVMOptions -d64 -Xmx 2G -Xms 2G -XX:+UseParNewGC -XX:ParallelGCThreads=4 -XX:+CMSParallelRemarkEnabled -XX:+UseConcMarkSweepGC -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+AggressiveOpts -XX:+UseNUMA -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:MaxGCPauseMillis=30  -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=4000 -XX:ReservedCodeCacheSize=1024m -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing
