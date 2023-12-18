# Minecraft FPS Boosting JVM Arguments

JVM arguments that you can use in your launcher to increase your Minecraft performance. Originally made for people like me who want to run Minecraft with their low-end potatoes, but it can also work for those with access to higher-end PCs - though the results may be diminished.

---

## JVM Args for my PC
`-XX:+UnlockExperimentalVMOptions -d64 -Xmx 6G -Xms 6G -XX:+DisableExplicitGC -XX:+UseParNewGC -XX:ParallelGCThreads=12 -XX:+CMSParallelRemarkEnabled -XX:+UseConcMarkSweepGC -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+AggressiveOpts -XX:+UseNUMA -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:MaxGCPauseMillis=25  -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=10000 -XX:ReservedCodeCacheSize=3072m -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing -XX:+UseStringDeduplication`

#

### Adjust these arguments to better suit your PC

- `-d64` - Makes the Java application (Minecraft) run as a 64-bit program, which allows it to use what your 64-bit OS has to offer to its fullest potential; only use this if your operating system is 64-bit / x64 (not 32-bit / x86) - otherwise, remove this parameter as Java sets this for 32-bit by default.
- `-Xmx 6G` - Sets the maximum allocated RAM of the Java application (Minecraft) at launch; you should always leave at least 1 GB left over (2 GB is highly recommended if it is available, which is what I did for my 8 GB RAM PC) for your system.
- `-Xms 6G` - Sets the initial allocated RAM of the Java application (Minecraft) at launch; this value should be the same as the maximum allocated RAM to reduce amount of garbage collection the program has to do.
- `-XX:ReservedCodeCacheSize=3072m` - Sets the cache size for reserved code that the Java application (Minecraft) might reuse. This should be half of the RAM allocated to Minecraft; in my case, I have allocated 6 GB (6144 MB) of RAM, so I will use 3072m (3 GB).
- `-XX:ParallelGCThreads=12` - Sets the maximum logical processors (threads) the Java application (Minecraft) can use; my CPU has 12 threads, so I set it to 12. You can find yours in the Performance tab of Task Manager.

#

### Notes :
- If it crashes, first try disabling `Connected Textures` in Minecraft's video settings before deleting any arguments.
- Please keep in mind that some arguments may cause your client to crash depending on your PC specifications (and maybe your Minecraft version?) and you may have to experiment around with changing some values or even deleting some of them in order for it to work.
- I have seen the `-Xmn` argument being used in other Minecraft FPS boosting JVM arguments but I do not use it because by default `-Xmn` is selected internally according to your system's capabilities.
- I have also seen `-XX:+UseCompressedOops` being used, but it is only available for and already automatically enabled on 64-bit programs.

#

<h3 align="center">Analytics</h3>
<p align="center"><img src="https://repobeats.axiom.co/api/embed/e28e426f1ba5e497bda1f10e45d7fb58d09587b9.svg" alt="Repobeats analytics image"/></p>
