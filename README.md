# Minecraft FPS-Boosting JVM Arguments
JVM arguments that you can use in your launcher to increase your Minecraft performance. Originally made for people like me who want to run Minecraft with their low-end potatoes, but it can also work for those with access to higher-end PCs - though the results may be diminished.

## JVM Args for my PC
```
-XX:+UnlockExperimentalVMOptions -d64 -Xmx 6G -Xms 6G -XX:+DisableExplicitGC -XX:+UseParNewGC -XX:ParallelGCThreads=12 -XX:+CMSParallelRemarkEnabled -XX:+UseConcMarkSweepGC -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+AggressiveOpts -XX:+UseNUMA -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:MaxGCPauseMillis=25  -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=10000 -XX:ReservedCodeCacheSize=3072m -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing -XX:+UseStringDeduplication
```

### Adjust these arguments to better suit your PC
- `-d64` makes the Java application (Minecraft) run as a 64-bit program, which allows it to use the capabilities of 64-bit machines; only use this if your operating system is 64-bit (x64) and not 32-bit (x86), otherwise, remove this parameter as Java sets this for 32-bit by default.
- `-Xmx 6G` sets the maximum allocated RAM of the Java application (Minecraft) to 6 GB; you should always leave at least 1 GB left over (2 GB is highly recommended if it is available, which is what I did for my 8 GB RAM PC) for your system.
- `-Xms 6G` sets the initial allocated RAM of Minecraft to 6 GB; this value should be the same as the maximum allocated RAM to reduce amount of garbage collection the program has to do.
- `-XX:ReservedCodeCacheSize=3072m` sets the cache size for reserved code that Minecraft might reuse to 3072 MB. This should be half of the RAM allocated to Minecraft; in my case, I have allocated 6 GB (6144 MB) of RAM with `-Xmx` and `-Xms` as seen above, so I set it to 3072m (3 GB).
- `-XX:ParallelGCThreads=12` sets the maximum threads the Minecraft can use to 12. For example, my CPU has 12 logical processors, so I set it to 12. You can find the number of logical processors on your PC in the Performance tab of Task Manager on the Windows operating system.

### Notes :
- If it crashes, first try disabling `Connected Textures` in Minecraft's video settings before deleting any arguments.
- Please keep in mind that some arguments may cause your client to crash depending on your PC specifications (and maybe your Minecraft version?) and you may have to experiment around with changing some values or even deleting some of them in order for it to work.
- I have seen the `-Xmn` argument being used in other Minecraft FPS boosting JVM arguments but I do not use it because by default `-Xmn` is selected internally according to your system's capabilities.
- I have also seen `-XX:+UseCompressedOops` being used in other "fps boost" launch option configurations, but it is only available for and already enabled automatically on 64-bit programs (which can be enabled using the `-d64` argument).
