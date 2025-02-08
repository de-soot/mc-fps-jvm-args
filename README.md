# Minecraft FPS-boosting JVM Arguments

JVM (Java Virtual Machine) arguments that you can use in your launcher to increase your Minecraft performance. For people who want to run Minecraft on their low-end potatoes, but it can also be used to squeeze out performance in higher-end PCs (although with diminishing returns).

# The JVM Args

These are the arguments I used to run Minecraft on [Legacy Launcher](https://docs.llaun.ch/en/launcher/source) (a.k.a. the original TLauncher, which unfortunately had its name stolen and got DMCA'd by Mojang):

`
-XX:+UnlockExperimentalVMOptions -d64 -Xmx 6G -Xms 6G -XX:+DisableExplicitGC -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:ParallelGCThreads=12 -XX:+CMSParallelRemarkEnabled -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+AggressiveOpts -XX:+UseNUMA -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:MaxGCPauseMillis=50  -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=10000 -XX:ReservedCodeCacheSize=3072M -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing -XX:+UseStringDeduplication
`

## For Java 17

Below are JVM arguments submitted by [913ms](https://github.com/de-soot/mc-fps-jvm-args/issues/3) for Java 17:

`
-XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+UseG1GC -XX:ParallelGCThreads=12 -XX:-UseGCOverheadLimit -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:MaxGCPauseMillis=50 -XX:SurvivorRatio=8 -XX:TargetSurvivorRatio=90 -XX:MaxTenuringThreshold=15 -XX:SoftRefLRUPolicyMSPerMB=10000 -XX:ReservedCodeCacheSize=3072M -XX:+UseStringDeduplication
`

## Adjusting Arguments

It is crucial that you do not simply copy and paste these args into your launcher's JVM arguments box. Many of the parameters of the args are highly dependant on many factors, including your device specs, Java version, Minecraft launcher, so what might work for me most likely will not work for you.

- `-d64` makes the Java application (Minecraft) run as a 64-bit program, which allows it to use the capabilities of 64-bit machines; only use this if your operating system is 64-bit (x86_64) and not 32-bit (i386), otherwise, remove this parameter as Java sets this for 32-bit by default.
- `-Xmx 6G` sets the maximum allocated RAM of the Java application (Minecraft) to 6 GB; you should leave at least 1 GB left over (2 GB is recommended if available) for the rest of your system not dedicated to Minecraft. Note that this arg, as well as `-Xms` below, does not work for third-party launchers like Prism Launcher and MultiMC, so feel free to remove it if you do not use the official Minecraft launcher and use the built-in RAM allocation settings instead.
- `-Xms 6G` sets the minimum allocated RAM of Minecraft to 6 GB; this value implicitly sets the target RAM allocation for the garbage collector, so it should be close to the maximum allocated RAM to reduce amount of garbage collection the program does. Note that this arg, as well as `-Xmx` above, does not work for third-party launchers like Prism Launcher and MultiMC, so feel free to remove it if you do not use the official Minecraft launcher and use the built-in RAM allocation settings instead.
- `-XX:ReservedCodeCacheSize=3072M` sets the cache size allowed for reserved code that Minecraft might reuse to 3072 MB (3 GB). This should be around half of the RAM allocated to Minecraft; in my case, I have allocated 6 GB (6144 MB) of RAM, so I set it to 3 GB (3072 MB -> `3072M`).
- `-XX:ParallelGCThreads=12` sets the maximum threads the Minecraft can use to 12. For example, my CPU has 12 logical processors, so I set it to 12. If you are using Windows, you can find the number of logical processors in the Performance tab of Task Manager.
- `-XX:+UseG1GC` has mixed results. It worked for 913ms, but it did not for me and a [few](https://www.reddit.com/r/feedthebeast/comments/b1ol67/garbage_collection_freeze_troubleshooting) [others](https://www.reddit.com/r/feedthebeast/comments/5jhuk9/modded_mc_and_memory_usage_a_history_with_a). Experiment with this argument to see if it works for you.
- `-XX:MaxGCPauseMillis=50` sets the "maximum" time the garbage collector (GC) can freeze to 50 miliseconds, which is the time for 1 tick (there are 20 ticks in a second, so each tick is 1/20 seconds). This "maximum" is really only just a target, so your GC will just ignore it if it cannot reach it.

## Notes
- Please do keep in mind that some arguments may cause your client to crash depending on your PC specifications, Minecraft version, Java version, and Minecraft launcher (e.g. Prism Launcher, MultiMC). You may have to experiment around with changing or removing some values in order for it to work.
- Note that the args `-Xmx` and `-Xms` do not work for third-party launchers like Prism Launcher and MultiMC, so feel free to remove it if you do not use the official Minecraft launcher and use the built-in RAM allocation settings instead.
- If it crashes, first try disabling `Connected Textures` in Minecraft's video settings before removing any arguments.
- I have seen the `-Xmn` argument being used in other Minecraft FPS boosting JVM arguments, but it is not included because `-Xmn` is selected internally according to your system's capabilities by default.
- I have also seen `-XX:+UseCompressedOops` being used in other "fps boost" launch option configurations, but it is only available for and already enabled automatically on 64-bit programs, making it redundant with the `-d64` argument.

# Contribution

If you find any incompatible JVM arguments for a specific launcher or Java version, please [report an issue](https://github.com/de-soot/mc-fps-jvm-args/issues) or [open a pull request](https://github.com/de-soot/mc-fps-jvm-args/pulls).

