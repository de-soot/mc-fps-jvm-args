# FPS-Boost-Minecraft-JVM-Arguments
JVM arguments that optimise your performance in Minecraft.

# The Arguments :
-XX:+UnlockExperimentalVMOptions -d64 –XX:+UseParallelGC -XX:ParallelGCThreads=4 XX:+AggressiveOpts -XX:+DisableExplicitGC -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:+UseNUMA -XX:+CMSParallelRemarkEnabled -XX:+UseAdaptiveGCBoundary -XX:-UseGCOverheadLimit -XX:+UseBiasedLocking -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -XX:+UseFastAccessorMethods -XX:+UseCompressedOops -XX:MaxGCPauseMillis=50 -XX:+OptimizeStringConcat -XX:+UseCodeCacheFlushing
