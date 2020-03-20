---
title: 在 Windows 上為 Apache Spark 應用程式構建 .NET
description: 瞭解如何在 Windows 上為 Apache Spark 應用程式構建 .NET。
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185750"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="65caa-103">瞭解如何在 Windows 上為 Apache Spark 應用程式構建 .NET</span><span class="sxs-lookup"><span data-stu-id="65caa-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="65caa-104">本文教您如何在 Windows 上為 Apache Spark 應用程式構建 .NET。</span><span class="sxs-lookup"><span data-stu-id="65caa-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65caa-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="65caa-105">Prerequisites</span></span>

<span data-ttu-id="65caa-106">如果您已經具備以下所有先決條件，請跳到[生成](#build)步驟。</span><span class="sxs-lookup"><span data-stu-id="65caa-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="65caa-107">下載並安裝**[.NET 核心 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - 安裝`dotnet`SDK 會將工具鏈添加到您的路徑中。</span><span class="sxs-lookup"><span data-stu-id="65caa-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="65caa-108">.NET 核心 2.1、2.2 和 3.1 支援。</span><span class="sxs-lookup"><span data-stu-id="65caa-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="65caa-109">安裝**[Visual Studio 2019（](https://www.visualstudio.com/downloads/)** 版本 16.3 或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="65caa-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="65caa-110">社區版本是完全免費的。</span><span class="sxs-lookup"><span data-stu-id="65caa-110">The Community version is completely free.</span></span> <span data-ttu-id="65caa-111">配置安裝時，至少包括以下元件：</span><span class="sxs-lookup"><span data-stu-id="65caa-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="65caa-112">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="65caa-112">.NET desktop development</span></span>
       * <span data-ttu-id="65caa-113">所有必需的元件</span><span class="sxs-lookup"><span data-stu-id="65caa-113">All Required Components</span></span>
         * <span data-ttu-id="65caa-114">.NET Framework 4.6.1 開發工具</span><span class="sxs-lookup"><span data-stu-id="65caa-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="65caa-115">.NET Core 跨平台開發</span><span class="sxs-lookup"><span data-stu-id="65caa-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="65caa-116">所有必需的元件</span><span class="sxs-lookup"><span data-stu-id="65caa-116">All Required Components</span></span>
  3. <span data-ttu-id="65caa-117">安裝**[JAVA 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**。</span><span class="sxs-lookup"><span data-stu-id="65caa-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="65caa-118">為您的作業系統選取適當版本。</span><span class="sxs-lookup"><span data-stu-id="65caa-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="65caa-119">例如，適用于 Windows x64 電腦的*jdk-8u201-windows-x64.exe。*</span><span class="sxs-lookup"><span data-stu-id="65caa-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="65caa-120">使用安裝程式進行安裝，並驗證您能夠從命令`java`行運行。</span><span class="sxs-lookup"><span data-stu-id="65caa-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="65caa-121">安裝**[阿帕奇馬文3.6.0+。](https://maven.apache.org/download.cgi)**</span><span class="sxs-lookup"><span data-stu-id="65caa-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="65caa-122">下載 [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip)。</span><span class="sxs-lookup"><span data-stu-id="65caa-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="65caa-123">解壓縮到本機目錄。</span><span class="sxs-lookup"><span data-stu-id="65caa-123">Extract to a local directory.</span></span> <span data-ttu-id="65caa-124">例如，[C：\bin_apache-maven-3.6.0。\*</span><span class="sxs-lookup"><span data-stu-id="65caa-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="65caa-125">將 Apache Maven 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。</span><span class="sxs-lookup"><span data-stu-id="65caa-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="65caa-126">例如 *，C：\bin_apache-maven-3.6.0\bin*。</span><span class="sxs-lookup"><span data-stu-id="65caa-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="65caa-127">驗證是否能夠從命令列`mvn`運行。</span><span class="sxs-lookup"><span data-stu-id="65caa-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="65caa-128">安裝**[阿帕奇火花2.3+。](https://spark.apache.org/downloads.html)**</span><span class="sxs-lookup"><span data-stu-id="65caa-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="65caa-129">下載[Apache Spark 2.3+](https://spark.apache.org/downloads.html)並將其提取到本地資料夾中（例如 *，C：\bin_spark-2.3.2-bin-hadoop2.7），\*使用[7-zip](https://www.7-zip.org/)。（支援的火花版本是 2.3、* 2.4.0、 2.4.1、 2.4.3 和 2.4.4）</span><span class="sxs-lookup"><span data-stu-id="65caa-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="65caa-130">添加新[的環境變數](https://www.java.com/en/download/help/path.xml)`SPARK_HOME`。</span><span class="sxs-lookup"><span data-stu-id="65caa-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="65caa-131">例如，[C：\bin_spark-2.3.2-bin-hadoop2.7。\*</span><span class="sxs-lookup"><span data-stu-id="65caa-131">For example, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - <span data-ttu-id="65caa-132">將 Apache Spark 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。</span><span class="sxs-lookup"><span data-stu-id="65caa-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="65caa-133">例如 *，C：\bin_spark-2.3.2-bin-hadoop2.7\bin*。</span><span class="sxs-lookup"><span data-stu-id="65caa-133">For example, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="65caa-134">驗證是否能夠從命令列`spark-shell`運行。</span><span class="sxs-lookup"><span data-stu-id="65caa-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="65caa-135">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="65caa-135">Sample console output:</span></span>

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

        </details>

  6. <span data-ttu-id="65caa-136">安裝**[WinUtils](https://github.com/steveloughran/winutils)**。</span><span class="sxs-lookup"><span data-stu-id="65caa-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="65caa-137">從`winutils.exe` [WinUtils 存儲庫](https://github.com/steveloughran/winutils)下載二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="65caa-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="65caa-138">您應該選擇使用 Spark 分發編譯的 Hadoop 版本。</span><span class="sxs-lookup"><span data-stu-id="65caa-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="65caa-139">對於考試，使用有 2.7.1 用於 Spark 2.3.2。</span><span class="sxs-lookup"><span data-stu-id="65caa-139">For exammple, use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="65caa-140">將`winutils.exe`二進位檔案保存到您選擇的目錄中。</span><span class="sxs-lookup"><span data-stu-id="65caa-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="65caa-141">例如 *，C：\hadoop\bin。*</span><span class="sxs-lookup"><span data-stu-id="65caa-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="65caa-142">設置為`HADOOP_HOME`使用 winutils.exe（無 bin）反映目錄。</span><span class="sxs-lookup"><span data-stu-id="65caa-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="65caa-143">例如，使用命令列：</span><span class="sxs-lookup"><span data-stu-id="65caa-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="65caa-144">將 PATH 環境變數`%HADOOP_HOME%\bin`設置為包括 。</span><span class="sxs-lookup"><span data-stu-id="65caa-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="65caa-145">例如，使用命令列：</span><span class="sxs-lookup"><span data-stu-id="65caa-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="65caa-146">在移動到下一節之前，`dotnet``java`請確保能夠`mvn`從`spark-shell`命令列運行 、、。</span><span class="sxs-lookup"><span data-stu-id="65caa-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="65caa-147">感覺有更好的方法嗎？</span><span class="sxs-lookup"><span data-stu-id="65caa-147">Feel there is a better way?</span></span> <span data-ttu-id="65caa-148">[打開問題](https://github.com/dotnet/spark/issues)，隨時作出貢獻。</span><span class="sxs-lookup"><span data-stu-id="65caa-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="65caa-149">如果更新了任何環境變數，則可能需要命令列的新實例。</span><span class="sxs-lookup"><span data-stu-id="65caa-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="65caa-150">Build</span><span class="sxs-lookup"><span data-stu-id="65caa-150">Build</span></span>

<span data-ttu-id="65caa-151">在本指南的其餘部分中，您需要將 Apache Spark 的 .NET 存儲庫克隆到您的電腦中。</span><span class="sxs-lookup"><span data-stu-id="65caa-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="65caa-152">您可以選擇克隆存儲庫的任何位置。</span><span class="sxs-lookup"><span data-stu-id="65caa-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="65caa-153">例如，[C：github]點網火花\*。</span><span class="sxs-lookup"><span data-stu-id="65caa-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="65caa-154">為阿帕奇火花斯卡拉擴展層構建 .NET</span><span class="sxs-lookup"><span data-stu-id="65caa-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="65caa-155">提交 .NET 應用程式時，Apache Spark 的 .NET 具有用 Scala 編寫的必要邏輯，該邏輯通知 Apache Spark 如何處理您的請求（例如，請求創建新 Spark 會話、請求將資料從 .NET 端傳輸到 JVM 端等）。</span><span class="sxs-lookup"><span data-stu-id="65caa-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="65caa-156">此邏輯可以在[.NET 中找到 Spark Scala 原始程式碼](https://github.com/dotnet/spark/tree/master/src/scala)。</span><span class="sxs-lookup"><span data-stu-id="65caa-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="65caa-157">無論您是使用 .NET 框架還是 .NET Core，都需要為 Apache Spark Scala 擴展層構建 .NET：</span><span class="sxs-lookup"><span data-stu-id="65caa-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="65caa-158">您應該會看到為支援的 Spark 版本創建的 JAR：</span><span class="sxs-lookup"><span data-stu-id="65caa-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="65caa-159">為 Spark 應用程式範例構建 .NET</span><span class="sxs-lookup"><span data-stu-id="65caa-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="65caa-160">本節介紹如何為 Apache Spark 構建 .NET[的應用程式範例](https://github.com/dotnet/spark/tree/master/examples)。</span><span class="sxs-lookup"><span data-stu-id="65caa-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="65caa-161">這些步驟將有助於瞭解任何 .NET 用於 Spark 應用程式的總體構建過程。</span><span class="sxs-lookup"><span data-stu-id="65caa-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="65caa-162">將視覺化工作室用於 .NET 框架</span><span class="sxs-lookup"><span data-stu-id="65caa-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="65caa-163">在`src\csharp\Microsoft.Spark.sln`Visual Studio 中`Microsoft.Spark.CSharp.Examples`打開並在`examples`資料夾下生成專案（這反過來還將生成 .NET 繫結項目目）。</span><span class="sxs-lookup"><span data-stu-id="65caa-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="65caa-164">如果需要，可以在`Microsoft.Spark.Examples`專案中編寫自己的代碼（此示例中的"input_file.json"是一個 json 檔，該檔包含要創建資料框的資料：</span><span class="sxs-lookup"><span data-stu-id="65caa-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="65caa-165">生成成功後，您將看到輸出目錄中生成的相應二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="65caa-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="65caa-166">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="65caa-166">Sample console output:</span></span>

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="65caa-167">將 .NET 核心 CLI 用於 .NET 內核</span><span class="sxs-lookup"><span data-stu-id="65caa-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="65caa-168">我們目前正在為 Spark .NET 自動化 .NET 核心構建。</span><span class="sxs-lookup"><span data-stu-id="65caa-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="65caa-169">在此之前，我們感謝您手動執行某些步驟的耐心。</span><span class="sxs-lookup"><span data-stu-id="65caa-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="65caa-170">生成工作人員：</span><span class="sxs-lookup"><span data-stu-id="65caa-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="65caa-171">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="65caa-171">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. <span data-ttu-id="65caa-172">生成示例：</span><span class="sxs-lookup"><span data-stu-id="65caa-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="65caa-173">示例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="65caa-173">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="65caa-174">為 Spark 應用程式範例運行 .NET</span><span class="sxs-lookup"><span data-stu-id="65caa-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="65caa-175">生成示例後，無論目標是 .NET Framework`spark-submit`還是 .NET Core，運行示例都將完成。</span><span class="sxs-lookup"><span data-stu-id="65caa-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="65caa-176">請確保您已遵循[先決條件](#prerequisites)部分並安裝了 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="65caa-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="65caa-177">將`DOTNET_WORKER_DIR`或`PATH`環境變數設置為包括已生成`Microsoft.Spark.Worker`二進位檔案的路徑（例如 *，C：github_dotnet_spark_x_x_x_s_x_microsoft.Spark.Worker_debug_net461*表示 .NET Framework，C：_gitnet_dotnet-spark_工件*\Microsoft.Spark.Worker_Debug_netcoreapp2.1_win10-x64_發佈*為 .NET Core）：</span><span class="sxs-lookup"><span data-stu-id="65caa-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="65caa-178">打開 Powershell 並轉到已生成應用二進位的目錄（例如 *，C：github_dotnet_spark_sas_microsoft.Spark.CSharp.示例_debug_net461*的 .NET *Framework，C：_gitnet_spark_t_t_t_s_t_s_t_sat_Sa.Spark.CSharp.example_debug_netcore2.1_win10-x64_發佈*為 .NET Core）：</span><span class="sxs-lookup"><span data-stu-id="65caa-178">Open Powershell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="65caa-179">運行應用遵循基本結構：</span><span class="sxs-lookup"><span data-stu-id="65caa-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="65caa-180">下面是您可以運行的一些示例：</span><span class="sxs-lookup"><span data-stu-id="65caa-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="65caa-181">**[微軟.Spark.示例.Sql.Batch.基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="65caa-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="65caa-182">**[微軟.Spark.示例.Sql.流式處理.結構化網路WordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="65caa-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="65caa-183">**[微軟.Spark.示例.Sql.Streaming.結構化卡夫卡WordCount（可訪問）](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="65caa-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="65caa-184">**[微軟.Spark.示例.Sql.Streaming.結構化卡夫卡WordCount（提供jars）](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="65caa-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
