---
title: 在 Ubuntu 上為 Apache Spark 應用程式構建 .NET
description: 瞭解如何在 Ubuntu 上為 Apache Spark 應用程式構建 .NET
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 6dd6f60bb89a51c47fe17182fc47de818cd00b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187563"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>瞭解如何在 Ubuntu 上為 Apache Spark 應用程式構建 .NET

本文教您如何在 Ubuntu 上為 Apache Spark 應用程式構建 .NET。

## <a name="prerequisites"></a>必要條件

如果您已經具備以下所有先決條件，請跳到[生成](#build)步驟。

1. 下載並安裝**[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** 或**[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - 安裝 SDK 會`dotnet`將工具鏈添加到您的路徑中。  .NET 核心 2.1、2.2 和 3.1 支援。

2. 安裝**[OpenJDK 8](https://openjdk.java.net/install/)**。

   - 可以使用以下命令：

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * 驗證是否能夠從命令列`java`運行。

      java -版本輸出示例：

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * 如果您已經安裝了多個 OpenJDK 版本，並且想要選擇 OpenJDK 8，請使用以下命令：

      ```bash
      sudo update-alternatives --config java
      ```

3. 安裝**[阿帕奇馬文3.6.0+。](https://maven.apache.org/download.cgi)**

   * 執行以下命令：

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

       請注意，關閉終端時，這些環境變數將丟失。 如果希望更改是永久性的，請將`export`行添加到檔中。 `~/.bashrc`

   * 驗證您能夠從命令列`mvn`運行

       示例 mvn -版本輸出：

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. 安裝**[阿帕奇火花2.3+。](https://spark.apache.org/downloads.html)**
下載[Apache Spark 2.3+](https://spark.apache.org/downloads.html)並將其提取到本地資料夾中（例如， `~/bin/spark-2.3.2-bin-hadoop2.7` （支援的火花版本為 2.3.*、2.4.0、2.4.1、2.4.3 和 2.4.4）

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * 添加必要的[環境變數](https://www.java.com/en/download/help/path.xml)`SPARK_HOME`（例如`~/bin/spark-2.3.2-bin-hadoop2.7/`）和`PATH`（例如 ） `$SPARK_HOME/bin:$PATH`

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      請注意，關閉終端時，這些環境變數將丟失。 如果希望更改是永久性的，請將`export`行添加到檔中。 `~/.bashrc`

   * 驗證是否能夠從命令列`spark-shell`運行。

      示例主控台輸出：

      ```
      Welcome to
            ____              __
           / __/__  ___ _____/ /__
          _\ \/ _ \/ _ `/ __/  '_/
         /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
            /_/

      Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
      Type in expressions to have them evaluated.
      Type :help for more information.

      scala> sc
      res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
      ```

在移動到下一節之前，`dotnet``java`請確保能夠`mvn`從`spark-shell`命令列運行 。。" 感覺有更好的方法嗎？ 請[打開一個問題](https://github.com/dotnet/spark/issues)，並隨時作出貢獻。

## <a name="build"></a>Build

在本指南的其餘部分中，您需要將 Apache Spark 的 .NET 存儲庫克隆到您的電腦中，例如 。 `~/dotnet.spark/`

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>為 Spark Scala 擴展圖層構建 .NET

提交 .NET 應用程式時，Apache Spark 的 .NET 具有用 Scala 編寫的必要邏輯，該邏輯通知 Apache Spark 如何處理您的請求（例如，請求創建新 Spark 會話、請求將資料從 .NET 端傳輸到 JVM 端等）。 此邏輯可以在[阿帕奇 Spark Scala 原始程式碼的 .NET](https://github.com/dotnet/spark/tree/master/src/scala)中找到。

下一步是為 Apache Spark Scala 擴展層構建 .NET：

```bash
cd src/scala
mvn clean package
```

您應該會看到為支援的 Spark 版本創建的 JAR：

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>使用 .NET 核心 CLI 生成 .NET 應用程式範例

本節介紹如何為 Apache Spark 構建 .NET[的應用程式範例](https://github.com/dotnet/spark/tree/master/examples)。 這些步驟將有助於瞭解任何 .NET 用於 Spark 應用程式的總體構建過程。

1. 生成工作人員：

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   示例主控台輸出：

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. 生成示例：

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   示例主控台輸出：

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a>為 Spark 應用程式範例運行 .NET

生成示例後，可以使用`spark-submit`提交 .NET Core 應用。 請確保您已遵循[先決條件](#prerequisites)部分並安裝了 Apache Spark。

1. 將`DOTNET_WORKER_DIR`或`PATH`環境變數設置為包括生成二進位`Microsoft.Spark.Worker`檔的路徑（例如， `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. 打開終端並轉到已生成應用二進位檔案的目錄（例如。 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. 運行應用遵循基本結構：

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   下面是您可以運行的一些示例：

   * **[微軟.Spark.示例.Sql.Batch.基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[微軟.Spark.示例.Sql.流式處理.結構化網路WordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[微軟.Spark.示例.Sql.Streaming.結構化卡夫卡WordCount（可訪問）](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[微軟.Spark.示例.Sql.Streaming.結構化卡夫卡WordCount（提供jars）](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
