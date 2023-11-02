# The JVM arguments :
-XX:+UnlockExperimentalVMOptions -d64 -Xmx 6G -Xms 6G -XX:+DisableExplicitGC -XX:+UseParNewGC -XX:ParallelGCThreads=12 -XX:+CMSParallelRemarkEnabled -XX:+UseConcMarkSweepGC -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+AggressiveOpts -XX:+UseNUMA -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:MaxGCPauseMillis=25  -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=6000 -XX:ReservedCodeCacheSize=3072m -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing

# Read these first to adjust the arguments to suit your system :

"-d64" - Makes the Java application (in this case, it's Minecraft) run as a 64-bit program, which allows it to use what your 64-bit OS has to offer; only use this if your operating system is 64-bit, otherwise remove this parameter.

"-Xmx 6G" - Sets the maximum allocated RAM to 6 GB of RAM to the Java application (in this case, it's Minecraft) at launch; you should always leave at least 1 GB left over (2 GB is recommended) for your system.

"-Xms 6G" - Sets the initial allocated RAM to 6 GB of RAM to the Java application (Minecraft) at launch; this value should be the same as the maximum allocated RAM to reduce amount of garbage collection the program has to do.

"-XX:ReservedCodeCacheSize=3072m" - Sets the cache size for reserved code that the Java application (in this case, it's Minecraft) might reuse. This should be half of the RAM allocated to Minecraft; in my case, I have allocated 6 GB (6144 MB) of RAM, so I will use 3072m (3 GB).

"-XX:SoftRefLRUPolicyMSPerMB=6000" - Tells the Java application (Minecraft) how much milliseconds to use per MB of soft references. For example: For example: if you have 1 GB to spare, use 2000; since I allocated 4 GB and have 2 GB to spare, I'll use 6000. Feel free to experiment with this value to get the best results.

"-XX:ParallelGCThreads=12" - Sets the maximum logical processors (threads) the Java application (in this case, it's Minecraft) can use; my CPU has 12 threads, so I set it to 12.
