# Explanations to the arguments; read these first to customise the settings to suit your system :

"-d64" - Makes Minecraft run as a 64-bit program; only use this if your operating system is 64-bit, otherwise remove this parameter.

"-Xmx 2G -Xms 2G" - Allocates 2 GB of RAM to Minecraft at launch; you should always leave at least 1 GB (2 GB is recommended) for your system.

"-XX:ReservedCodeCacheSize=1024m" - Sets the cache size for reserved code that Minecraft might reuse. This should be half of the RAM allocated to Minecraft; in my case, I have allocated 2 GB (2048 MB) of RAM, so I will use 1024m (1 GB).

"-XX:SoftRefLRUPolicyMSPerMB=4000" - Tells Minecraft how much milliseconds to use per MB of soft references. If you only allocated 1 GB to Minecraft, use 2000 instead; but since I allocated 2 GB, I use 4000.

"-XX:ParallelGCThreads=4" - Sets it to the amount of logical processors (threads) your CPU has.

# The Arguments :
-XX:+UnlockExperimentalVMOptions -d64 -Xmx 2G -Xms 2G –XX:+UseParallelGC -XX:ParallelGCThreads=4 XX:+AggressiveOpts -XX:+DisableExplicitGC -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:+UseNUMA -XX:+CMSParallelRemarkEnabled -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:+UseCompressedOops -XX:MaxGCPauseMillis=30  -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=4000 -XX:ReservedCodeCacheSize=1024m -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing
