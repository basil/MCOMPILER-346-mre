# MCOMPILER-346 Minimal Reproducible Example (MRE)

## Steps to reproduce

Ensure you are running Java 11:

```
$ mvn -version
Apache Maven 3.8.4 (9b656c72d54e5bacbed989b64718c159fe39b537)
Maven home: /opt/maven
Java version: 11.0.13, vendor: Ubuntu, runtime: /usr/lib/jvm/java-11-openjdk-amd64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.4.0-100-generic", arch: "amd64", family: "unix"
```

Then run `mvn clean verify`.

## Expected results

**Note:** These are the _actual_ results when running with `mvn clean verify -Dmaven.compiler.forceJavacCompilerUse=true`.

The expected result is that compilation should fail with an informative message stating what errors in the source code are preventing compilation.

```
[…]
[INFO] --- maven-compiler-plugin:3.10.0:compile (default-compile) @ plexus-compiler-bug-mre ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to src/jenkinsci/repro/target/classes
[INFO] -------------------------------------------------------------
[ERROR] COMPILATION ERROR :
[INFO] -------------------------------------------------------------
[ERROR] src/jenkinsci/repro/src/main/java/org/jenkinsci/test/acceptance/server/PooledJenkinsController.java:[12,47] error: package org.jenkinsci.test.acceptance.controller does not exist
[…]
[ERROR] src/jenkinsci/repro/src/main/java/org/jenkinsci/test/acceptance/server/PooledJenkinsController.java:[173,61] error: cannot find symbol
  symbol:   class LogListener
  location: class InstallLogger
[INFO] 26 errors
[INFO] -------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.714 s
[INFO] Finished at: 2022-03-04T16:37:17-08:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.10.0:compile (default-compile) on project plexus-compiler-bug-mre: Compilation failure: Compilation failure:
[ERROR] src/jenkinsci/repro/src/main/java/org/jenkinsci/test/acceptance/server/PooledJenkinsController.java:[12,47] error: package org.jenkinsci.test.acceptance.controller does not exist
[…]
[ERROR] src/jenkinsci/repro/src/main/java/org/jenkinsci/test/acceptance/server/PooledJenkinsController.java:[173,61] error: cannot find symbol
[ERROR]   symbol:   class LogListener
[ERROR]   location: class InstallLogger
[ERROR] -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
```

## Actual results

The build fails with an `AssertionError` and no informative message is printed.

```
[…]
[INFO] --- maven-compiler-plugin:3.10.0:compile (default-compile) @ plexus-compiler-bug-mre ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to src/jenkinsci/repro/target/classes
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.718 s
[INFO] Finished at: 2022-03-04T16:40:54-08:00
[INFO] ------------------------------------------------------------------------
---------------------------------------------------
constituent[0]: file:/opt/maven/conf/logging/
constituent[1]: file:/opt/maven/lib/plexus-sec-dispatcher-2.0.jar
constituent[2]: file:/opt/maven/lib/maven-resolver-impl-1.6.3.jar
constituent[3]: file:/opt/maven/lib/maven-resolver-provider-3.8.4.jar
constituent[4]: file:/opt/maven/lib/maven-resolver-spi-1.6.3.jar
constituent[5]: file:/opt/maven/lib/maven-settings-builder-3.8.4.jar
constituent[6]: file:/opt/maven/lib/commons-io-2.6.jar
constituent[7]: file:/opt/maven/lib/plexus-component-annotations-2.1.0.jar
constituent[8]: file:/opt/maven/lib/slf4j-api-1.7.32.jar
constituent[9]: file:/opt/maven/lib/maven-slf4j-provider-3.8.4.jar
constituent[10]: file:/opt/maven/lib/guava-25.1-android.jar
constituent[11]: file:/opt/maven/lib/maven-repository-metadata-3.8.4.jar
constituent[12]: file:/opt/maven/lib/wagon-provider-api-3.4.3.jar
constituent[13]: file:/opt/maven/lib/maven-settings-3.8.4.jar
constituent[14]: file:/opt/maven/lib/plexus-cipher-2.0.jar
constituent[15]: file:/opt/maven/lib/maven-model-3.8.4.jar
constituent[16]: file:/opt/maven/lib/maven-resolver-transport-wagon-1.6.3.jar
constituent[17]: file:/opt/maven/lib/maven-plugin-api-3.8.4.jar
constituent[18]: file:/opt/maven/lib/plexus-utils-3.3.0.jar
constituent[19]: file:/opt/maven/lib/wagon-http-3.4.3-shaded.jar
constituent[20]: file:/opt/maven/lib/javax.annotation-api-1.2.jar
constituent[21]: file:/opt/maven/lib/javax.inject-1.jar
constituent[22]: file:/opt/maven/lib/jcl-over-slf4j-1.7.32.jar
constituent[23]: file:/opt/maven/lib/maven-embedder-3.8.4.jar
constituent[24]: file:/opt/maven/lib/plexus-interpolation-1.26.jar
constituent[25]: file:/opt/maven/lib/maven-artifact-3.8.4.jar
constituent[26]: file:/opt/maven/lib/maven-core-3.8.4.jar
constituent[27]: file:/opt/maven/lib/org.eclipse.sisu.plexus-0.3.5.jar
constituent[28]: file:/opt/maven/lib/commons-cli-1.4.jar
constituent[29]: file:/opt/maven/lib/guice-4.2.2-no_aop.jar
constituent[30]: file:/opt/maven/lib/maven-model-builder-3.8.4.jar
constituent[31]: file:/opt/maven/lib/maven-resolver-util-1.6.3.jar
constituent[32]: file:/opt/maven/lib/maven-shared-utils-3.3.4.jar
constituent[33]: file:/opt/maven/lib/maven-compat-3.8.4.jar
constituent[34]: file:/opt/maven/lib/jansi-2.4.0.jar
constituent[35]: file:/opt/maven/lib/org.eclipse.sisu.inject-0.3.5.jar
constituent[36]: file:/opt/maven/lib/wagon-file-3.4.3.jar
constituent[37]: file:/opt/maven/lib/commons-lang3-3.8.1.jar
constituent[38]: file:/opt/maven/lib/maven-resolver-api-1.6.3.jar
constituent[39]: file:/opt/maven/lib/maven-builder-support-3.8.4.jar
constituent[40]: file:/opt/maven/lib/maven-resolver-connector-basic-1.6.3.jar
---------------------------------------------------
Exception in thread "main" java.lang.AssertionError
	at jdk.compiler/com.sun.tools.javac.util.Assert.error(Assert.java:155)
	at jdk.compiler/com.sun.tools.javac.util.Assert.check(Assert.java:46)
	at jdk.compiler/com.sun.tools.javac.comp.Modules.enter(Modules.java:247)
	at jdk.compiler/com.sun.tools.javac.main.JavaCompiler.readSourceFile(JavaCompiler.java:837)
	at jdk.compiler/com.sun.tools.javac.processing.JavacProcessingEnvironment$ImplicitCompleter.complete(JavacProcessingEnvironment.java:1535)
	at jdk.compiler/com.sun.tools.javac.code.Symbol.complete(Symbol.java:642)
	at jdk.compiler/com.sun.tools.javac.code.Symbol$ClassSymbol.complete(Symbol.java:1326)
	at jdk.compiler/com.sun.tools.javac.code.Type$ClassType.complete(Type.java:1140)
	at jdk.compiler/com.sun.tools.javac.code.Type$ClassType.getTypeArguments(Type.java:1066)
	at jdk.compiler/com.sun.tools.javac.code.Printer.visitClassType(Printer.java:237)
	at jdk.compiler/com.sun.tools.javac.code.Printer.visitClassType(Printer.java:52)
	at jdk.compiler/com.sun.tools.javac.code.Type$ClassType.accept(Type.java:993)
	at jdk.compiler/com.sun.tools.javac.code.Printer.visit(Printer.java:136)
	at jdk.compiler/com.sun.tools.javac.util.AbstractDiagnosticFormatter.formatArgument(AbstractDiagnosticFormatter.java:199)
	at jdk.compiler/com.sun.tools.javac.util.AbstractDiagnosticFormatter.formatArguments(AbstractDiagnosticFormatter.java:167)
	at jdk.compiler/com.sun.tools.javac.util.BasicDiagnosticFormatter.formatMessage(BasicDiagnosticFormatter.java:111)
	at jdk.compiler/com.sun.tools.javac.util.BasicDiagnosticFormatter.formatMessage(BasicDiagnosticFormatter.java:67)
	at jdk.compiler/com.sun.tools.javac.util.AbstractDiagnosticFormatter.formatArgument(AbstractDiagnosticFormatter.java:185)
	at jdk.compiler/com.sun.tools.javac.util.AbstractDiagnosticFormatter.formatArguments(AbstractDiagnosticFormatter.java:167)
	at jdk.compiler/com.sun.tools.javac.util.BasicDiagnosticFormatter.formatMessage(BasicDiagnosticFormatter.java:111)
	at jdk.compiler/com.sun.tools.javac.util.BasicDiagnosticFormatter.formatMessage(BasicDiagnosticFormatter.java:67)
	at jdk.compiler/com.sun.tools.javac.util.JCDiagnostic.getMessage(JCDiagnostic.java:788)
	at jdk.compiler/com.sun.tools.javac.api.ClientCodeWrapper$DiagnosticSourceUnwrapper.getMessage(ClientCodeWrapper.java:799)
	at org.codehaus.plexus.compiler.javac.JavaxToolsCompiler.compileInProcess(JavaxToolsCompiler.java:140)
	at org.codehaus.plexus.compiler.javac.JavacCompiler.performCompile(JavacCompiler.java:178)
	at org.apache.maven.plugin.compiler.AbstractCompilerMojo.execute(AbstractCompilerMojo.java:1199)
	at org.apache.maven.plugin.compiler.CompilerMojo.execute(CompilerMojo.java:198)
	at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo(DefaultBuildPluginManager.java:137)
	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:210)
	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:156)
	at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:148)
	at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:117)
	at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:81)
	at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:56)
	at org.apache.maven.lifecycle.internal.LifecycleStarter.execute(LifecycleStarter.java:128)
	at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:305)
	at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:192)
	at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:105)
	at org.apache.maven.cli.MavenCli.execute(MavenCli.java:972)
	at org.apache.maven.cli.MavenCli.doMain(MavenCli.java:293)
	at org.apache.maven.cli.MavenCli.main(MavenCli.java:196)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:282)
	at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:225)
	at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:406)
	at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:347)
```
