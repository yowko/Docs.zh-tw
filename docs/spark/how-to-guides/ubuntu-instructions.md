---
title: 在 Ubuntu 上建立 Apache Spark 應用程式的 .NET
description: 瞭解如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 77daad7298c41d21054db9174f30a8d1ed12648d
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687788"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>瞭解如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET

本文會教您如何在 Ubuntu 上建立 Apache Spark 應用程式的 .NET。

## <a name="prerequisites"></a>先決條件

如果您已經擁有下列所有必要條件，請跳至 [組建](#build) 步驟。

1. 下載並安裝 **[.Net Core 3.1 sdk](https://dotnet.microsoft.com/download/dotnet-core/3.1)** -安裝 sdk 會將 `dotnet` 工具鏈新增至您的路徑。  支援 .NET Core 2.1、2.2 和3.1。

2. 安裝 **[OpenJDK 8](https://openjdk.java.net/install/)**。

   - 您可以使用下列命令：

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * 確認您可以 `java` 從命令列執行。

      JAVA-版本輸出範例：

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * 如果您已安裝多個 OpenJDK 版本，而且想要選取 OpenJDK 8，請使用下列命令：

      ```bash
      sudo update-alternatives --config java
      ```

3. 安裝 **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**。

   * 執行下列命令：

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       請注意，當您關閉終端時，這些環境變數將會遺失。 如果您想要永久變更，請將這 `export` 幾行新增至您的檔案 `~/.bashrc` 。

   * 確認您可以 `mvn` 從命令列執行

       範例 mvn-版本輸出：

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. 安裝 **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**。
下載 [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) ，並將其解壓縮至本機資料夾 (例如 `~/bin/spark-3.0.1-bin-hadoop2.7`) 。  (支援的 spark 版本為 2.3. *、2.4.0、2.4.1、2.4.3、2.4.4、2.4.5、2.4.6、2.4.7 版、3.0.0 和 3.0.1) 

   ```bash
   tar -xvzf /path/to/spark-3.0.1-bin-hadoop2.7.tgz -C ~/bin/spark-3.0.1-bin-hadoop2.7
   ```

   * 新增必要的 [環境變數](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (例如 `~/bin/spark-3.0.1-bin-hadoop2.7/`) 和 `PATH` (例如 `$SPARK_HOME/bin:$PATH`) 

      ```bash
      export SPARK_HOME=~/bin/spark-3.0.1-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      請注意，當您關閉終端時，這些環境變數將會遺失。 如果您想要永久變更，請將這 `export` 幾行新增至您的檔案 `~/.bashrc` 。

   * 確認您可以 `spark-shell` 從命令列執行。

      範例主控台輸出：

      ```
      Welcome to
            ____              __
           / __/__  ___ _____/ /__
          _\ \/ _ \/ _ `/ __/  '_/
         /___/ .__/\_,_/_/ /_/\_\   version 3.0.1
            /_/

      Using Scala version 2.12.10 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
      Type in expressions to have them evaluated.
      Type :help for more information.

      scala> sc
      res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
      ```

`dotnet` `java` `mvn` `spark-shell` 在移至下一節之前，請先確定您能夠從命令列執行。 覺得有更好的方法？ 請 [開啟問題](https://github.com/dotnet/spark/issues) ，並歡迎您提供貢獻。

## <a name="build"></a>Build

針對本指南的其餘部分，您必須將 Apache Spark 存放庫的 .NET 複製到您的電腦中，例如 `~/dotnet.spark/` 。

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>為 Spark Scala 擴充功能層建立 .NET

當您提交 .NET 應用程式時，適用于 Apache Spark 的 .NET 具有以 Scala 撰寫的必要邏輯，以通知 Apache Spark 如何處理您的要求 (例如，要求建立新的 Spark 會話、要求將資料從 .NET 端傳送到 JVM 端等。 ) 。 您可以在 .Net 中找到 [Apache Spark Scala 原始程式碼](https://github.com/dotnet/spark/tree/master/src/scala)的這個邏輯。

下一步是建立適用于 Apache Spark Scala 擴充層的 .NET：

```bash
cd src/scala
mvn clean package
```

您應該會看到針對支援的 Spark 版本所建立的 Jar：

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>使用 .NET Core CLI 建立 .NET 範例應用程式

本節說明如何針對 Apache Spark 建立適用于 .NET 的 [範例應用程式](https://github.com/dotnet/spark/tree/master/examples) 。 這些步驟將有助於瞭解任何適用于 Spark 應用程式之 .NET 的整體建築流程。

1. 建立背景工作角色：

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   範例主控台輸出：

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```

2. 建立範例：

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   範例主控台輸出：

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a>執行適用于 Spark 的 .NET 範例應用程式

建立範例之後，您可以使用 `spark-submit` 來提交您的 .Net Core 應用程式。 請確定您已遵循 [必要條件](#prerequisites) 一節並安裝 Apache Spark。

1. 設定 `DOTNET_WORKER_DIR` 或 `PATH` 環境變數，以包含 `Microsoft.Spark.Worker` 已產生二進位檔的路徑 (例如 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish`) 。

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

2. 開啟終端機，並移至您的應用程式二進位檔產生所在的目錄 (例如 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish`) 。

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

3. 執行應用程式的基本結構如下：

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   以下是您可以執行的一些範例：

   * **[Microsoft.Spark.Examples.Sql.Batch。基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[StructuredNetworkWordCount （範例）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[StructuredKafkaWordCount (maven 可存取的可存取)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[StructuredKafkaWordCount () 提供的 jar 範例。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
