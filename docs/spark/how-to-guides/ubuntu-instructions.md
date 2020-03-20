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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="7fc9a-103">瞭解如何在 Ubuntu 上為 Apache Spark 應用程式構建 .NET</span><span class="sxs-lookup"><span data-stu-id="7fc9a-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="7fc9a-104">本文教您如何在 Ubuntu 上為 Apache Spark 應用程式構建 .NET。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7fc9a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="7fc9a-105">Prerequisites</span></span>

<span data-ttu-id="7fc9a-106">如果您已經具備以下所有先決條件，請跳到[生成](#build)步驟。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="7fc9a-107">下載並安裝**[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** 或**[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - 安裝 SDK 會`dotnet`將工具鏈添加到您的路徑中。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="7fc9a-108">.NET 核心 2.1、2.2 和 3.1 支援。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="7fc9a-109">安裝**[OpenJDK 8](https://openjdk.java.net/install/)**。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="7fc9a-110">可以使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="7fc9a-111">驗證是否能夠從命令列`java`運行。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="7fc9a-112">java -版本輸出示例：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="7fc9a-113">如果您已經安裝了多個 OpenJDK 版本，並且想要選擇 OpenJDK 8，請使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="7fc9a-114">安裝**[阿帕奇馬文3.6.0+。](https://maven.apache.org/download.cgi)**</span><span class="sxs-lookup"><span data-stu-id="7fc9a-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="7fc9a-115">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-115">Run the following command:</span></span>

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

       <span data-ttu-id="7fc9a-116">請注意，關閉終端時，這些環境變數將丟失。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="7fc9a-117">如果希望更改是永久性的，請將`export`行添加到檔中。 `~/.bashrc`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="7fc9a-118">驗證您能夠從命令列`mvn`運行</span><span class="sxs-lookup"><span data-stu-id="7fc9a-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="7fc9a-119">示例 mvn -版本輸出：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-119">Sample mvn -version output:</span></span>

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="7fc9a-120">安裝**[阿帕奇火花2.3+。](https://spark.apache.org/downloads.html)**</span><span class="sxs-lookup"><span data-stu-id="7fc9a-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="7fc9a-121">下載[Apache Spark 2.3+](https://spark.apache.org/downloads.html)並將其提取到本地資料夾中（例如， `~/bin/spark-2.3.2-bin-hadoop2.7`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="7fc9a-122">（支援的火花版本為 2.3.\*、2.4.0、2.4.1、2.4.3 和 2.4.4）</span><span class="sxs-lookup"><span data-stu-id="7fc9a-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="7fc9a-123">添加必要的[環境變數](https://www.java.com/en/download/help/path.xml)`SPARK_HOME`（例如`~/bin/spark-2.3.2-bin-hadoop2.7/`）和`PATH`（例如 ） `$SPARK_HOME/bin:$PATH`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="7fc9a-124">請注意，關閉終端時，這些環境變數將丟失。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="7fc9a-125">如果希望更改是永久性的，請將`export`行添加到檔中。 `~/.bashrc`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="7fc9a-126">驗證是否能夠從命令列`spark-shell`運行。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="7fc9a-127">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-127">Sample console output:</span></span>

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

<span data-ttu-id="7fc9a-128">在移動到下一節之前，`dotnet``java`請確保能夠`mvn`從`spark-shell`命令列運行 。。"</span><span class="sxs-lookup"><span data-stu-id="7fc9a-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="7fc9a-129">感覺有更好的方法嗎？</span><span class="sxs-lookup"><span data-stu-id="7fc9a-129">Feel there is a better way?</span></span> <span data-ttu-id="7fc9a-130">請[打開一個問題](https://github.com/dotnet/spark/issues)，並隨時作出貢獻。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="7fc9a-131">Build</span><span class="sxs-lookup"><span data-stu-id="7fc9a-131">Build</span></span>

<span data-ttu-id="7fc9a-132">在本指南的其餘部分中，您需要將 Apache Spark 的 .NET 存儲庫克隆到您的電腦中，例如 。 `~/dotnet.spark/`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="7fc9a-133">為 Spark Scala 擴展圖層構建 .NET</span><span class="sxs-lookup"><span data-stu-id="7fc9a-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="7fc9a-134">提交 .NET 應用程式時，Apache Spark 的 .NET 具有用 Scala 編寫的必要邏輯，該邏輯通知 Apache Spark 如何處理您的請求（例如，請求創建新 Spark 會話、請求將資料從 .NET 端傳輸到 JVM 端等）。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="7fc9a-135">此邏輯可以在[阿帕奇 Spark Scala 原始程式碼的 .NET](https://github.com/dotnet/spark/tree/master/src/scala)中找到。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="7fc9a-136">下一步是為 Apache Spark Scala 擴展層構建 .NET：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="7fc9a-137">您應該會看到為支援的 Spark 版本創建的 JAR：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="7fc9a-138">使用 .NET 核心 CLI 生成 .NET 應用程式範例</span><span class="sxs-lookup"><span data-stu-id="7fc9a-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="7fc9a-139">本節介紹如何為 Apache Spark 構建 .NET[的應用程式範例](https://github.com/dotnet/spark/tree/master/examples)。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="7fc9a-140">這些步驟將有助於瞭解任何 .NET 用於 Spark 應用程式的總體構建過程。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="7fc9a-141">生成工作人員：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="7fc9a-142">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-142">Sample console output:</span></span>

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

2. <span data-ttu-id="7fc9a-143">生成示例：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="7fc9a-144">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-144">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="7fc9a-145">為 Spark 應用程式範例運行 .NET</span><span class="sxs-lookup"><span data-stu-id="7fc9a-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="7fc9a-146">生成示例後，可以使用`spark-submit`提交 .NET Core 應用。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="7fc9a-147">請確保您已遵循[先決條件](#prerequisites)部分並安裝了 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="7fc9a-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="7fc9a-148">將`DOTNET_WORKER_DIR`或`PATH`環境變數設置為包括生成二進位`Microsoft.Spark.Worker`檔的路徑（例如， `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="7fc9a-149">打開終端並轉到已生成應用二進位檔案的目錄（例如。 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`</span><span class="sxs-lookup"><span data-stu-id="7fc9a-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="7fc9a-150">運行應用遵循基本結構：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="7fc9a-151">下面是您可以運行的一些示例：</span><span class="sxs-lookup"><span data-stu-id="7fc9a-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="7fc9a-152">**[微軟.Spark.示例.Sql.Batch.基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="7fc9a-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="7fc9a-153">**[微軟.Spark.示例.Sql.流式處理.結構化網路WordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="7fc9a-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="7fc9a-154">**[微軟.Spark.示例.Sql.Streaming.結構化卡夫卡WordCount（可訪問）](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="7fc9a-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="7fc9a-155">**[微軟.Spark.示例.Sql.Streaming.結構化卡夫卡WordCount（提供jars）](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="7fc9a-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
