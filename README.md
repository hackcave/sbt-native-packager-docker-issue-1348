# sbt-native-packager-docker-issue-1348

Original bug report at [https://github.com/sbt/sbt-native-packager/issues/1348](https://github.com/sbt/sbt-native-packager/issues/1348)

To reproduce the bug:

```bash
git clone https://github.com/hackcave/sbt-native-packager-docker-issue-1348.git
cd sbt-native-packager-docker-issue-1348 && sbt docker:publishLocal
```

It fails with this error:
```log
[info] Step 5/15 : COPY opt /opt
[error] COPY failed: stat /var/lib/docker/tmp/docker-builder390126844/opt: no such file or directory                                 
[error] java.lang.RuntimeException: Nonzero exit value: 1
[error]         at com.typesafe.sbt.packager.docker.DockerPlugin$.publishLocalDocker(DockerPlugin.scala:622)
[error]         at com.typesafe.sbt.packager.docker.DockerPlugin$.$anonfun$projectSettings$53(DockerPlugin.scala:250)
[error]         at com.typesafe.sbt.packager.docker.DockerPlugin$.$anonfun$projectSettings$53$adapted(DockerPlugin.scala:242)
[error]         at scala.Function1.$anonfun$compose$1(Function1.scala:49)
[error]         at sbt.internal.util.$tilde$greater.$anonfun$$u2219$1(TypeFunctions.scala:62)
[error]         at sbt.std.Transform$$anon$4.work(Transform.scala:67)
[error]         at sbt.Execute.$anonfun$submit$2(Execute.scala:281)
[error]         at sbt.internal.util.ErrorHandling$.wideConvert(ErrorHandling.scala:19)
[error]         at sbt.Execute.work(Execute.scala:290)
[error]         at sbt.Execute.$anonfun$submit$1(Execute.scala:281)
[error]         at sbt.ConcurrentRestrictions$$anon$4.$anonfun$submitValid$1(ConcurrentRestrictions.scala:178)
[error]         at sbt.CompletionService$$anon$2.call(CompletionService.scala:37)
[error]         at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
[error]         at java.base/java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:515)
[error]         at java.base/java.util.concurrent.FutureTask.run(FutureTask.java:264)
[error]         at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
[error]         at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
[error]         at java.base/java.lang.Thread.run(Thread.java:834)
[error] (Docker / publishLocal) Nonzero exit value: 1
```

