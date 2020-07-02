---
title: 在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET
description: 瞭解如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 078d080f4ce293875d8fea8c3e804736b28a2eaf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620933"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="04f1a-103">瞭解如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="04f1a-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="04f1a-104">本文會教您如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET。</span><span class="sxs-lookup"><span data-stu-id="04f1a-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="04f1a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="04f1a-105">Prerequisites</span></span>

<span data-ttu-id="04f1a-106">如果您已經擁有下列所有必要條件，請跳至[組建](#build)步驟。</span><span class="sxs-lookup"><span data-stu-id="04f1a-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="04f1a-107">下載並安裝**[.Net core 2.1 sdk](https://dotnet.microsoft.com/download/dotnet-core/2.1)** 或**[.NET core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** -安裝 SDK 會將工具鏈新增 `dotnet` 至您的路徑。</span><span class="sxs-lookup"><span data-stu-id="04f1a-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="04f1a-108">支援 .NET Core 2.1、2.2 和3.1。</span><span class="sxs-lookup"><span data-stu-id="04f1a-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="04f1a-109">安裝**[OpenJDK 8](https://openjdk.java.net/install/)**。</span><span class="sxs-lookup"><span data-stu-id="04f1a-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="04f1a-110">您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="04f1a-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="04f1a-111">確認您能夠 `java` 從命令列執行。</span><span class="sxs-lookup"><span data-stu-id="04f1a-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="04f1a-112">JAVA 版本的範例輸出：</span><span class="sxs-lookup"><span data-stu-id="04f1a-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="04f1a-113">如果您已安裝多個 OpenJDK 版本，而且想要選取 [OpenJDK 8]，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="04f1a-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="04f1a-114">安裝**[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**。</span><span class="sxs-lookup"><span data-stu-id="04f1a-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="04f1a-115">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="04f1a-115">Run the following command:</span></span>

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

       <span data-ttu-id="04f1a-116">請注意，當您關閉終端機時，這些環境變數將會遺失。</span><span class="sxs-lookup"><span data-stu-id="04f1a-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="04f1a-117">如果您想要永久變更，請將這些 `export` 行新增至您的檔案 `~/.bashrc` 。</span><span class="sxs-lookup"><span data-stu-id="04f1a-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="04f1a-118">確認您能夠 `mvn` 從命令列執行</span><span class="sxs-lookup"><span data-stu-id="04f1a-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="04f1a-119">範例 mvn-版本輸出：</span><span class="sxs-lookup"><span data-stu-id="04f1a-119">Sample mvn -version output:</span></span>

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="04f1a-120">安裝**[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**。</span><span class="sxs-lookup"><span data-stu-id="04f1a-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="04f1a-121">下載[Apache Spark 2.3 +](https://spark.apache.org/downloads.html) ，並將其解壓縮至本機資料夾（例如 `~/bin/spark-2.3.2-bin-hadoop2.7` ）。</span><span class="sxs-lookup"><span data-stu-id="04f1a-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="04f1a-122">（支援的 spark 版本為 2.3. \*、2.4.0、2.4.1、2.4.3 和2.4.4）</span><span class="sxs-lookup"><span data-stu-id="04f1a-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="04f1a-123">新增必要的[環境變數](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` （例如， `~/bin/spark-2.3.2-bin-hadoop2.7/` ）和 `PATH` （例如 `$SPARK_HOME/bin:$PATH` ）</span><span class="sxs-lookup"><span data-stu-id="04f1a-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="04f1a-124">請注意，當您關閉終端機時，這些環境變數將會遺失。</span><span class="sxs-lookup"><span data-stu-id="04f1a-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="04f1a-125">如果您想要永久變更，請將這些 `export` 行新增至您的檔案 `~/.bashrc` 。</span><span class="sxs-lookup"><span data-stu-id="04f1a-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="04f1a-126">確認您能夠 `spark-shell` 從命令列執行。</span><span class="sxs-lookup"><span data-stu-id="04f1a-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="04f1a-127">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="04f1a-127">Sample console output:</span></span>

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

<span data-ttu-id="04f1a-128">在 `dotnet` 移到下一節之前，請確定您能夠 `java` `mvn` `spark-shell` 從命令列執行、、。</span><span class="sxs-lookup"><span data-stu-id="04f1a-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="04f1a-129">覺得有更好的方法嗎？</span><span class="sxs-lookup"><span data-stu-id="04f1a-129">Feel there is a better way?</span></span> <span data-ttu-id="04f1a-130">請提出[問題](https://github.com/dotnet/spark/issues)，並隨意參與。</span><span class="sxs-lookup"><span data-stu-id="04f1a-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="04f1a-131">Build</span><span class="sxs-lookup"><span data-stu-id="04f1a-131">Build</span></span>

<span data-ttu-id="04f1a-132">在本指南的其餘部分，您必須將 Apache Spark 存放庫的 .NET 複製到您的電腦，例如 `~/dotnet.spark/` 。</span><span class="sxs-lookup"><span data-stu-id="04f1a-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="04f1a-133">建立適用于 Spark Scala 擴充功能層的 .NET</span><span class="sxs-lookup"><span data-stu-id="04f1a-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="04f1a-134">當您提交 .NET 應用程式時，.NET for Apache Spark 具有以 Scala 撰寫的必要邏輯，會通知 Apache Spark 如何處理您的要求（例如，要求建立新的 Spark 會話、要求將資料從 .NET 端傳輸到 JVM 端等等）。</span><span class="sxs-lookup"><span data-stu-id="04f1a-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="04f1a-135">您可以在[適用于 Apache Spark Scala 的 .Net 原始程式碼](https://github.com/dotnet/spark/tree/master/src/scala)中找到此邏輯。</span><span class="sxs-lookup"><span data-stu-id="04f1a-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="04f1a-136">下一步是建立適用于 Apache Spark Scala 擴充層的 .NET：</span><span class="sxs-lookup"><span data-stu-id="04f1a-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="04f1a-137">您應該會看到針對支援的 Spark 版本所建立的 Jar：</span><span class="sxs-lookup"><span data-stu-id="04f1a-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="04f1a-138">使用 .NET Core CLI 建立 .NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="04f1a-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="04f1a-139">本節說明如何為 Apache Spark 建立適用于 .NET 的[範例應用程式](https://github.com/dotnet/spark/tree/master/examples)。</span><span class="sxs-lookup"><span data-stu-id="04f1a-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="04f1a-140">這些步驟將協助您瞭解任何適用于 Spark 應用程式的 .NET 的整體建立流程。</span><span class="sxs-lookup"><span data-stu-id="04f1a-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="04f1a-141">建立背景工作：</span><span class="sxs-lookup"><span data-stu-id="04f1a-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="04f1a-142">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="04f1a-142">Sample console output:</span></span>

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

2. <span data-ttu-id="04f1a-143">建立範例：</span><span class="sxs-lookup"><span data-stu-id="04f1a-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="04f1a-144">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="04f1a-144">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="04f1a-145">執行適用于 Spark 的 .NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="04f1a-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="04f1a-146">建立範例之後，您可以使用 `spark-submit` 來提交 .Net Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="04f1a-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="04f1a-147">請確定您已遵循[必要條件](#prerequisites)一節，並已安裝 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="04f1a-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="04f1a-148">將 `DOTNET_WORKER_DIR` 或 `PATH` 環境變數設定為包含 `Microsoft.Spark.Worker` 已產生二進位檔的路徑（例如 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish` ）。</span><span class="sxs-lookup"><span data-stu-id="04f1a-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="04f1a-149">開啟終端機，並移至已產生應用程式二進位檔的目錄（例如 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish` ）。</span><span class="sxs-lookup"><span data-stu-id="04f1a-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="04f1a-150">執行您的應用程式會遵循基本結構：</span><span class="sxs-lookup"><span data-stu-id="04f1a-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="04f1a-151">以下是您可以執行的一些範例：</span><span class="sxs-lookup"><span data-stu-id="04f1a-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="04f1a-152">**[Microsoft.Spark.Examples.Sql.Batch。基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="04f1a-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="04f1a-153">**[StructuredNetworkWordCount 的範例中。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="04f1a-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="04f1a-154">**[StructuredKafkaWordCount （可供存取 maven）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="04f1a-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="04f1a-155">**[StructuredKafkaWordCount （所提供的 jar）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="04f1a-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
