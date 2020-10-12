---
title: 在 Ubuntu 上建立 Apache Spark 應用程式的 .NET
description: 瞭解如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dfe105bb1549560ebdd2526a8441c4e2c5d141bf
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955058"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="43a99-103">瞭解如何在 Ubuntu 上建立適用于 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="43a99-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="43a99-104">本文會教您如何在 Ubuntu 上建立 Apache Spark 應用程式的 .NET。</span><span class="sxs-lookup"><span data-stu-id="43a99-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43a99-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="43a99-105">Prerequisites</span></span>

<span data-ttu-id="43a99-106">如果您已經擁有下列所有必要條件，請跳至 [組建](#build) 步驟。</span><span class="sxs-lookup"><span data-stu-id="43a99-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="43a99-107">下載並安裝 **[.Net core 2.1 sdk](https://dotnet.microsoft.com/download/dotnet-core/2.1)** 或 **[.NET core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** -安裝 SDK 會將工具鏈新增 `dotnet` 至您的路徑。</span><span class="sxs-lookup"><span data-stu-id="43a99-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="43a99-108">支援 .NET Core 2.1、2.2 和3.1。</span><span class="sxs-lookup"><span data-stu-id="43a99-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="43a99-109">安裝 **[OpenJDK 8](https://openjdk.java.net/install/)**。</span><span class="sxs-lookup"><span data-stu-id="43a99-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="43a99-110">您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="43a99-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="43a99-111">確認您可以 `java` 從命令列執行。</span><span class="sxs-lookup"><span data-stu-id="43a99-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="43a99-112">JAVA-版本輸出範例：</span><span class="sxs-lookup"><span data-stu-id="43a99-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="43a99-113">如果您已安裝多個 OpenJDK 版本，而且想要選取 OpenJDK 8，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="43a99-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="43a99-114">安裝 **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**。</span><span class="sxs-lookup"><span data-stu-id="43a99-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="43a99-115">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="43a99-115">Run the following command:</span></span>

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

       <span data-ttu-id="43a99-116">請注意，當您關閉終端時，這些環境變數將會遺失。</span><span class="sxs-lookup"><span data-stu-id="43a99-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="43a99-117">如果您想要永久變更，請將這 `export` 幾行新增至您的檔案 `~/.bashrc` 。</span><span class="sxs-lookup"><span data-stu-id="43a99-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="43a99-118">確認您可以 `mvn` 從命令列執行</span><span class="sxs-lookup"><span data-stu-id="43a99-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="43a99-119">範例 mvn-版本輸出：</span><span class="sxs-lookup"><span data-stu-id="43a99-119">Sample mvn -version output:</span></span>

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="43a99-120">安裝 **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**。</span><span class="sxs-lookup"><span data-stu-id="43a99-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="43a99-121">下載 [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) ，並將其解壓縮至本機資料夾 (例如 `~/bin/spark-2.3.2-bin-hadoop2.7`) 。</span><span class="sxs-lookup"><span data-stu-id="43a99-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="43a99-122"> (支援的 spark 版本為 2.3.\ *、2.4.0、2.4.1、2.4.3 和 2.4.4) </span><span class="sxs-lookup"><span data-stu-id="43a99-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="43a99-123">新增必要的 [環境變數](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (例如 `~/bin/spark-2.3.2-bin-hadoop2.7/`) 和 `PATH` (例如 `$SPARK_HOME/bin:$PATH`) </span><span class="sxs-lookup"><span data-stu-id="43a99-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="43a99-124">請注意，當您關閉終端時，這些環境變數將會遺失。</span><span class="sxs-lookup"><span data-stu-id="43a99-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="43a99-125">如果您想要永久變更，請將這 `export` 幾行新增至您的檔案 `~/.bashrc` 。</span><span class="sxs-lookup"><span data-stu-id="43a99-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="43a99-126">確認您可以 `spark-shell` 從命令列執行。</span><span class="sxs-lookup"><span data-stu-id="43a99-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="43a99-127">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="43a99-127">Sample console output:</span></span>

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

<span data-ttu-id="43a99-128">`dotnet` `java` `mvn` `spark-shell` 在移至下一節之前，請先確定您能夠從命令列執行。</span><span class="sxs-lookup"><span data-stu-id="43a99-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="43a99-129">覺得有更好的方法？</span><span class="sxs-lookup"><span data-stu-id="43a99-129">Feel there is a better way?</span></span> <span data-ttu-id="43a99-130">請 [開啟問題](https://github.com/dotnet/spark/issues) ，並歡迎您提供貢獻。</span><span class="sxs-lookup"><span data-stu-id="43a99-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="43a99-131">Build</span><span class="sxs-lookup"><span data-stu-id="43a99-131">Build</span></span>

<span data-ttu-id="43a99-132">針對本指南的其餘部分，您必須將 Apache Spark 存放庫的 .NET 複製到您的電腦中，例如 `~/dotnet.spark/` 。</span><span class="sxs-lookup"><span data-stu-id="43a99-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="43a99-133">為 Spark Scala 擴充功能層建立 .NET</span><span class="sxs-lookup"><span data-stu-id="43a99-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="43a99-134">當您提交 .NET 應用程式時，適用于 Apache Spark 的 .NET 具有以 Scala 撰寫的必要邏輯，以通知 Apache Spark 如何處理您的要求 (例如，要求建立新的 Spark 會話、要求將資料從 .NET 端傳送到 JVM 端等。 ) 。</span><span class="sxs-lookup"><span data-stu-id="43a99-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="43a99-135">您可以在 .Net 中找到 [Apache Spark Scala 原始程式碼](https://github.com/dotnet/spark/tree/master/src/scala)的這個邏輯。</span><span class="sxs-lookup"><span data-stu-id="43a99-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="43a99-136">下一步是建立適用于 Apache Spark Scala 擴充層的 .NET：</span><span class="sxs-lookup"><span data-stu-id="43a99-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="43a99-137">您應該會看到針對支援的 Spark 版本所建立的 Jar：</span><span class="sxs-lookup"><span data-stu-id="43a99-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="43a99-138">使用 .NET Core CLI 建立 .NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="43a99-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="43a99-139">本節說明如何針對 Apache Spark 建立適用于 .NET 的 [範例應用程式](https://github.com/dotnet/spark/tree/master/examples) 。</span><span class="sxs-lookup"><span data-stu-id="43a99-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="43a99-140">這些步驟將有助於瞭解任何適用于 Spark 應用程式之 .NET 的整體建築流程。</span><span class="sxs-lookup"><span data-stu-id="43a99-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="43a99-141">建立背景工作角色：</span><span class="sxs-lookup"><span data-stu-id="43a99-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="43a99-142">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="43a99-142">Sample console output:</span></span>

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

2. <span data-ttu-id="43a99-143">建立範例：</span><span class="sxs-lookup"><span data-stu-id="43a99-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="43a99-144">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="43a99-144">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="43a99-145">執行適用于 Spark 的 .NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="43a99-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="43a99-146">建立範例之後，您可以使用 `spark-submit` 來提交您的 .Net Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="43a99-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="43a99-147">請確定您已遵循 [必要條件](#prerequisites) 一節並安裝 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="43a99-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="43a99-148">設定 `DOTNET_WORKER_DIR` 或 `PATH` 環境變數，以包含 `Microsoft.Spark.Worker` 已產生二進位檔的路徑 (例如 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`) 。</span><span class="sxs-lookup"><span data-stu-id="43a99-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="43a99-149">開啟終端機，並移至您的應用程式二進位檔產生所在的目錄 (例如 `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`) 。</span><span class="sxs-lookup"><span data-stu-id="43a99-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="43a99-150">執行應用程式的基本結構如下：</span><span class="sxs-lookup"><span data-stu-id="43a99-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="43a99-151">以下是您可以執行的一些範例：</span><span class="sxs-lookup"><span data-stu-id="43a99-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="43a99-152">**[Microsoft.Spark.Examples.Sql.Batch。基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="43a99-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="43a99-153">**[StructuredNetworkWordCount （範例）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="43a99-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="43a99-154">**[StructuredKafkaWordCount (maven 可存取的可存取) ](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="43a99-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="43a99-155">**[StructuredKafkaWordCount () 提供的 jar 範例。 ](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="43a99-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
