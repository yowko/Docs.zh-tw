---
title: 在 Windows 上建立適用于 Apache Spark 應用程式的 .NET
description: 瞭解如何在 Windows 上建立適用于 Apache Spark 應用程式的 .NET。
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e6dec09f7d3e8d478cdcccf9df1c3e72d5f884eb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928033"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="d3e42-103">瞭解如何在 Windows 上建立適用于 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="d3e42-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="d3e42-104">本文會教您如何在 Windows 上建立適用于 Apache Spark 應用程式的 .NET。</span><span class="sxs-lookup"><span data-stu-id="d3e42-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3e42-105">必要條件：</span><span class="sxs-lookup"><span data-stu-id="d3e42-105">Prerequisites</span></span>

<span data-ttu-id="d3e42-106">如果您已經擁有下列所有必要條件，請跳至[組建](#build)步驟。</span><span class="sxs-lookup"><span data-stu-id="d3e42-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="d3e42-107">下載並安裝 **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** -安裝 SDK 會將 `dotnet` 工具鏈新增至您的路徑。</span><span class="sxs-lookup"><span data-stu-id="d3e42-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="d3e42-108">支援 .NET Core 2.1、2.2 和3.1。</span><span class="sxs-lookup"><span data-stu-id="d3e42-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="d3e42-109">安裝 **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** （版本16.3 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="d3e42-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="d3e42-110">此社區版本完全免費。</span><span class="sxs-lookup"><span data-stu-id="d3e42-110">The Community version is completely free.</span></span> <span data-ttu-id="d3e42-111">設定安裝時，請至少包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="d3e42-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="d3e42-112">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="d3e42-112">.NET desktop development</span></span>
       * <span data-ttu-id="d3e42-113">所有必要元件</span><span class="sxs-lookup"><span data-stu-id="d3e42-113">All Required Components</span></span>
         * <span data-ttu-id="d3e42-114">.NET Framework 4.6.1 開發工具</span><span class="sxs-lookup"><span data-stu-id="d3e42-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="d3e42-115">.NET Core 跨平台開發</span><span class="sxs-lookup"><span data-stu-id="d3e42-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="d3e42-116">所有必要元件</span><span class="sxs-lookup"><span data-stu-id="d3e42-116">All Required Components</span></span>
  3. <span data-ttu-id="d3e42-117">安裝 **[JAVA 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** 。</span><span class="sxs-lookup"><span data-stu-id="d3e42-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span> 
     - <span data-ttu-id="d3e42-118">為您的作業系統選取適當的版本，例如，適用于 Win x64 電腦的 jdk-8u201-windows-x64。</span><span class="sxs-lookup"><span data-stu-id="d3e42-118">Select the appropriate version for your operating system e.g., jdk-8u201-windows-x64.exe for Win x64 machine.</span></span>
     - <span data-ttu-id="d3e42-119">使用安裝程式進行安裝，並確認您能夠從命令列執行 `java`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-119">Install using the installer and verify you are able to run `java` from your command-line.</span></span>
  4. <span data-ttu-id="d3e42-120">安裝 **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** 。</span><span class="sxs-lookup"><span data-stu-id="d3e42-120">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="d3e42-121">下載 [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip)。</span><span class="sxs-lookup"><span data-stu-id="d3e42-121">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
     - <span data-ttu-id="d3e42-122">解壓縮至本機目錄，例如，`C:\bin\apache-maven-3.6.0\`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-122">Extract to a local directory e.g., `C:\bin\apache-maven-3.6.0\`.</span></span>
     - <span data-ttu-id="d3e42-123">將 Apache Maven 新增至您的[PATH 環境變數](https://www.java.com/en/download/help/path.xml)，例如 `C:\bin\apache-maven-3.6.0\bin`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-123">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\apache-maven-3.6.0\bin`.</span></span>
     - <span data-ttu-id="d3e42-124">確認您能夠從命令列執行 `mvn`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-124">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="d3e42-125">安裝 **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** 。</span><span class="sxs-lookup"><span data-stu-id="d3e42-125">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="d3e42-126">下載[Apache Spark 2.3 +](https://spark.apache.org/downloads.html) ，並使用[7-zip](https://www.7-zip.org/)將它解壓縮至本機資料夾（例如，`C:\bin\spark-2.3.2-bin-hadoop2.7\`）。</span><span class="sxs-lookup"><span data-stu-id="d3e42-126">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`) using [7-zip](https://www.7-zip.org/).</span></span> <span data-ttu-id="d3e42-127">（支援的 spark 版本為 2.3. \*、2.4.0、2.4.1、2.4.3 和2.4.4）</span><span class="sxs-lookup"><span data-stu-id="d3e42-127">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="d3e42-128">[新增環境變數](https://www.java.com/en/download/help/path.xml)`SPARK_HOME` 例如，`C:\bin\spark-2.3.2-bin-hadoop2.7\`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-128">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - <span data-ttu-id="d3e42-129">將 Apache Spark 新增至您的[PATH 環境變數](https://www.java.com/en/download/help/path.xml)，例如，`C:\bin\spark-2.3.2-bin-hadoop2.7\bin`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-129">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span></span>

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - <span data-ttu-id="d3e42-130">確認您能夠從命令列執行 `spark-shell`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-130">Verify you are able to run `spark-shell` from your command-line.</span></span>        
        <span data-ttu-id="d3e42-131">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="d3e42-131">Sample console output:</span></span>

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

  6. <span data-ttu-id="d3e42-132">安裝 **[winutils.exe](https://github.com/steveloughran/winutils)** 。</span><span class="sxs-lookup"><span data-stu-id="d3e42-132">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="d3e42-133">從[winutils.exe 存放庫](https://github.com/steveloughran/winutils)下載 `winutils.exe` 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="d3e42-133">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="d3e42-134">您應該選取用來編譯 Spark 發佈的 Hadoop 版本，例如使用 Spark 2.3.2 的 hadoop 2.7.1。</span><span class="sxs-lookup"><span data-stu-id="d3e42-134">You should select the version of Hadoop the Spark distribution was compiled with, e.g. use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="d3e42-135">將 `winutils.exe` 二進位檔儲存到您選擇的目錄中，例如，`C:\hadoop\bin`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-135">Save `winutils.exe` binary to a directory of your choice e.g., `C:\hadoop\bin`.</span></span>
     - <span data-ttu-id="d3e42-136">設定 `HADOOP_HOME` 以反映 winutils.exe 的目錄（不含 bin）。</span><span class="sxs-lookup"><span data-stu-id="d3e42-136">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="d3e42-137">例如，使用命令列：</span><span class="sxs-lookup"><span data-stu-id="d3e42-137">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="d3e42-138">將 PATH 環境變數設定為包含 `%HADOOP_HOME%\bin`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-138">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="d3e42-139">例如，使用命令列：</span><span class="sxs-lookup"><span data-stu-id="d3e42-139">For instance, using command-line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="d3e42-140">在移至下一節之前，請確定您能夠從命令列執行 `dotnet`、`java`、`mvn``spark-shell`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-140">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="d3e42-141">覺得有更好的方法嗎？</span><span class="sxs-lookup"><span data-stu-id="d3e42-141">Feel there is a better way?</span></span> <span data-ttu-id="d3e42-142">請提出[問題](https://github.com/dotnet/spark/issues)，並隨意參與。</span><span class="sxs-lookup"><span data-stu-id="d3e42-142">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="d3e42-143">如果更新任何環境變數，可能需要新的命令列實例。</span><span class="sxs-lookup"><span data-stu-id="d3e42-143">A new instance of the command-line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="d3e42-144">組建</span><span class="sxs-lookup"><span data-stu-id="d3e42-144">Build</span></span>

<span data-ttu-id="d3e42-145">在本指南的其餘部分，您必須將 Apache Spark 存放庫的 .NET 複製到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="d3e42-145">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="d3e42-146">您可以為複製的存放庫選擇任何位置，例如 `C:\github\dotnet-spark\`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-146">You can choose any location for the cloned repository, e.g., `C:\github\dotnet-spark\`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="d3e42-147">Apache Spark Scala extensions 層的組建 .NET</span><span class="sxs-lookup"><span data-stu-id="d3e42-147">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="d3e42-148">當您提交 .NET 應用程式時，.NET for Apache Spark 具有以 Scala 撰寫的必要邏輯，會通知 Apache Spark 如何處理您的要求（例如，要求建立新的 Spark 會話、要求將資料從 .NET 端傳輸到 JVM 端等等）。</span><span class="sxs-lookup"><span data-stu-id="d3e42-148">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="d3e42-149">您可以在[適用于 Spark 的 .Net Scala 原始程式碼](https://github.com/dotnet/spark/tree/master/src/scala)中找到此邏輯。</span><span class="sxs-lookup"><span data-stu-id="d3e42-149">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="d3e42-150">無論您使用的是 .NET Framework 或 .NET Core，都必須建立 .NET for Apache Spark Scala 擴充層：</span><span class="sxs-lookup"><span data-stu-id="d3e42-150">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package 
```

<span data-ttu-id="d3e42-151">您應該會看到針對支援的 Spark 版本所建立的 Jar：</span><span class="sxs-lookup"><span data-stu-id="d3e42-151">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="d3e42-152">建立適用于 Spark 的 .NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="d3e42-152">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="d3e42-153">本節說明如何為 Apache Spark 建立適用于 .NET 的[範例應用程式](https://github.com/dotnet/spark/tree/master/examples)。</span><span class="sxs-lookup"><span data-stu-id="d3e42-153">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="d3e42-154">這些步驟將協助您瞭解任何適用于 Spark 應用程式的 .NET 的整體建立流程。</span><span class="sxs-lookup"><span data-stu-id="d3e42-154">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="d3e42-155">使用 .NET Framework 的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3e42-155">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="d3e42-156">在 Visual Studio 中開啟 `src\csharp\Microsoft.Spark.sln`，並在 `examples` 資料夾底下建立 `Microsoft.Spark.CSharp.Examples` 專案（這也會建立 .NET 系結專案）。</span><span class="sxs-lookup"><span data-stu-id="d3e42-156">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="d3e42-157">如有需要，您可以在 `Microsoft.Spark.Examples` 專案中撰寫自己的程式碼（在此範例中，' input_file. json ' 是包含您想要用來建立資料框架之資料的 json 檔案）：</span><span class="sxs-lookup"><span data-stu-id="d3e42-157">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
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

     <span data-ttu-id="d3e42-158">組建成功之後，您會看到輸出目錄中產生的適當二進位檔。</span><span class="sxs-lookup"><span data-stu-id="d3e42-158">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>     
     <span data-ttu-id="d3e42-159">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="d3e42-159">Sample console output:</span></span>
     
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

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="d3e42-160">使用適用于 .NET Core 的 .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="d3e42-160">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="d3e42-161">我們目前正致力於將適用于 Spark .NET 的 .NET Core 組建自動化。</span><span class="sxs-lookup"><span data-stu-id="d3e42-161">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="d3e42-162">在那之前，我們非常感謝您的耐心等候您手動執行一些步驟。</span><span class="sxs-lookup"><span data-stu-id="d3e42-162">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="d3e42-163">建立背景工作：</span><span class="sxs-lookup"><span data-stu-id="d3e42-163">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      <span data-ttu-id="d3e42-164">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="d3e42-164">Sample console output:</span></span>

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

  2. <span data-ttu-id="d3e42-165">建立範例：</span><span class="sxs-lookup"><span data-stu-id="d3e42-165">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      <span data-ttu-id="d3e42-166">範例主控台輸出：</span><span class="sxs-lookup"><span data-stu-id="d3e42-166">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="d3e42-167">執行適用于 Spark 的 .NET 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="d3e42-167">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="d3e42-168">當您建立範例之後，不論您是以 .NET Framework 或 .NET Core 為目標，執行它們都會透過 `spark-submit`。</span><span class="sxs-lookup"><span data-stu-id="d3e42-168">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="d3e42-169">請確定您已遵循[必要條件](#prerequisites)一節，並已安裝 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="d3e42-169">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="d3e42-170">設定 `DOTNET_WORKER_DIR` 或 `PATH` 環境變數，以包含已產生 `Microsoft.Spark.Worker` 二進位檔的路徑（例如，.NET Framework 的 `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461`，適用于 .NET Core 的 `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish`）：</span><span class="sxs-lookup"><span data-stu-id="d3e42-170">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="d3e42-171">開啟 Powershell 並移至已產生應用程式二進位檔的目錄（例如，.NET Framework 的 `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461`，`C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` .NET Core）：</span><span class="sxs-lookup"><span data-stu-id="d3e42-171">Open Powershell and go to the directory where your app binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="d3e42-172">執行您的應用程式會遵循基本結構：</span><span class="sxs-lookup"><span data-stu-id="d3e42-172">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="d3e42-173">以下是您可以執行的一些範例：</span><span class="sxs-lookup"><span data-stu-id="d3e42-173">Here are some examples you can run:</span></span>

     - <span data-ttu-id="d3e42-174">**[Sql-dmo. .Sql. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="d3e42-174">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="d3e42-175">**[StructuredNetworkWordCount 的範例中。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="d3e42-175">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="d3e42-176">**[StructuredKafkaWordCount （可供存取 maven）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="d3e42-176">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="d3e42-177">**[StructuredKafkaWordCount （所提供的 jar）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="d3e42-177">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
