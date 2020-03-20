---
title: 開始使用適用於 Apache Spark 的 .NET
description: 瞭解如何在 Windows、MacOS 和 Ubuntu 上使用 .NET 核心運行 Apache Spark 應用的 .NET。
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187549"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="69cac-103">教程： 開始與 .NET 的阿帕奇火花</span><span class="sxs-lookup"><span data-stu-id="69cac-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="69cac-104">本教程教您如何在 Windows、MacOS 和 Ubuntu 上使用 .NET 核心運行 Apache Spark 應用的 .NET。</span><span class="sxs-lookup"><span data-stu-id="69cac-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="69cac-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="69cac-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="69cac-106">為 .NET 為 Apache Spark 準備您的環境</span><span class="sxs-lookup"><span data-stu-id="69cac-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="69cac-107">為 Apache Spark 應用程式編寫您的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="69cac-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="69cac-108">為 Apache Spark 應用程式構建並運行您的簡單 .NET</span><span class="sxs-lookup"><span data-stu-id="69cac-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="69cac-109">準備您的環境</span><span class="sxs-lookup"><span data-stu-id="69cac-109">Prepare your environment</span></span>

<span data-ttu-id="69cac-110">在開始編寫應用之前，需要設置一些先決條件依賴項。</span><span class="sxs-lookup"><span data-stu-id="69cac-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="69cac-111">如果可以從命令列`dotnet`環境中`java`運行`mvn` `spark-shell` 、、則環境已準備就緒，可以跳到下一節。</span><span class="sxs-lookup"><span data-stu-id="69cac-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="69cac-112">如果無法運行任何或所有命令，則執行以下步驟。</span><span class="sxs-lookup"><span data-stu-id="69cac-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="69cac-113">1. 安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="69cac-113">1. Install .NET</span></span>

<span data-ttu-id="69cac-114">要開始構建 .NET 應用，您需要下載並安裝 .NET SDK（軟體發展工具組）。</span><span class="sxs-lookup"><span data-stu-id="69cac-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="69cac-115">下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。</span><span class="sxs-lookup"><span data-stu-id="69cac-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="69cac-116">安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="69cac-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="69cac-117">安裝 .NET 核心 SDK 後，打開新的命令提示符或終端並運行`dotnet`。</span><span class="sxs-lookup"><span data-stu-id="69cac-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="69cac-118">如果命令運行並列印出有關如何使用 dotnet 的資訊，則可以移動到下一步。</span><span class="sxs-lookup"><span data-stu-id="69cac-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="69cac-119">如果收到`'dotnet' is not recognized as an internal or external command`錯誤，請確保在運行該命令之前打開了**新的**命令提示符或終端。</span><span class="sxs-lookup"><span data-stu-id="69cac-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="69cac-120">2. 安裝 JAVA</span><span class="sxs-lookup"><span data-stu-id="69cac-120">2. Install Java</span></span>

<span data-ttu-id="69cac-121">為 Windows 和 MacOS 安裝[JAVA 8.1，](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)為 Ubuntu[安裝 OpenJDK 8。](https://openjdk.java.net/install/)</span><span class="sxs-lookup"><span data-stu-id="69cac-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="69cac-122">為您的作業系統選取適當版本。</span><span class="sxs-lookup"><span data-stu-id="69cac-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="69cac-123">例如，為 Windows x64 電腦選擇**jdk-8u201-windows-x64.exe（** 如下所示）或適用于 MacOS 的**jdk-8u231-macosx-x64.dmg。**</span><span class="sxs-lookup"><span data-stu-id="69cac-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="69cac-124">然後，使用 命令`java`驗證安裝。</span><span class="sxs-lookup"><span data-stu-id="69cac-124">Then, use the command `java` to verify the installation.</span></span>

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="69cac-126">3. 安裝壓縮軟體</span><span class="sxs-lookup"><span data-stu-id="69cac-126">3. Install compression software</span></span>

<span data-ttu-id="69cac-127">Apache Spark 下載為壓縮 .tgz 檔。</span><span class="sxs-lookup"><span data-stu-id="69cac-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="69cac-128">使用提取程式（如[7-Zip](https://www.7-zip.org/)或[WinZip）](https://www.winzip.com/)提取檔。</span><span class="sxs-lookup"><span data-stu-id="69cac-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="69cac-129">4. 安裝阿帕奇火花</span><span class="sxs-lookup"><span data-stu-id="69cac-129">4. Install Apache Spark</span></span>

<span data-ttu-id="69cac-130">[下載並安裝阿帕奇火花](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="69cac-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="69cac-131">您需要從版本 2.3.\* 或 2.4.0、2.4.1、2.4.3 或 2.4.4（阿帕奇 Spark 的 NET 與其他版本的 Apache Spark 相容）中選擇。</span><span class="sxs-lookup"><span data-stu-id="69cac-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="69cac-132">以下步驟中使用的命令假定您[已下載並安裝了 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。</span><span class="sxs-lookup"><span data-stu-id="69cac-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="69cac-133">如果要使用其他版本，請將**2.4.1**替換為相應的版本號。</span><span class="sxs-lookup"><span data-stu-id="69cac-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="69cac-134">然後，提取 **.tar**檔和 Apache Spark 檔。</span><span class="sxs-lookup"><span data-stu-id="69cac-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="69cac-135">要提取嵌套的 **.tar**檔，</span><span class="sxs-lookup"><span data-stu-id="69cac-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="69cac-136">找到您下載的**spark-2.4.1-bin-hadoop2.7.tgz**檔。</span><span class="sxs-lookup"><span data-stu-id="69cac-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="69cac-137">按右鍵該檔，並在此處選擇**7-Zip-> 提取**。</span><span class="sxs-lookup"><span data-stu-id="69cac-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="69cac-138">**spark-2.4.1-bin-hadoop2.7.tar**與您下載的 **.tgz**檔一起創建。</span><span class="sxs-lookup"><span data-stu-id="69cac-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="69cac-139">要提取阿帕奇火花檔：</span><span class="sxs-lookup"><span data-stu-id="69cac-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="69cac-140">按右鍵**spark-2.4.1-bin-hadoop2.7.tar**並選擇**7-Zip-> 提取檔...**</span><span class="sxs-lookup"><span data-stu-id="69cac-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="69cac-141">在 **"提取到"** 欄位中輸入**C：\bin。**</span><span class="sxs-lookup"><span data-stu-id="69cac-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="69cac-142">取消選中 **"提取到**欄位"下的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="69cac-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="69cac-143">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69cac-143">Select **OK**.</span></span>
* <span data-ttu-id="69cac-144">Apache Spark 檔被提取到 C：\bin_spark-2.4.1-bin-hadoop2.7]</span><span class="sxs-lookup"><span data-stu-id="69cac-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7\</span></span>

![安裝 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="69cac-146">運行以下命令以設置用於在**Windows**上查找 Apache Spark 的環境變數：</span><span class="sxs-lookup"><span data-stu-id="69cac-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="69cac-147">運行以下命令以設置用於在**MacOS**和**Ubuntu**上定位 Apache Spark 的環境變數：</span><span class="sxs-lookup"><span data-stu-id="69cac-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="69cac-148">安裝所有內容並設置環境變數後，打開**新的**命令提示符或終端並運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69cac-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="69cac-149">如果命令運行並列印版本資訊，則可以移動到下一步。</span><span class="sxs-lookup"><span data-stu-id="69cac-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="69cac-150">如果收到`'spark-submit' is not recognized as an internal or external command`錯誤，請確保打開**新的**命令提示符。</span><span class="sxs-lookup"><span data-stu-id="69cac-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="69cac-151">5. 安裝 .NET 用於阿帕奇火花</span><span class="sxs-lookup"><span data-stu-id="69cac-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="69cac-152">從阿帕奇 Spark GitHub 的 .NET 下載[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases)版本。</span><span class="sxs-lookup"><span data-stu-id="69cac-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="69cac-153">例如，如果您在 Windows 電腦上並計畫使用 .NET Core，[請下載 Windows x64 netcoreapp3.1 版本](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)。</span><span class="sxs-lookup"><span data-stu-id="69cac-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="69cac-154">要提取 Microsoft.Spark.Worker：</span><span class="sxs-lookup"><span data-stu-id="69cac-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="69cac-155">找到您下載的**Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip**檔。</span><span class="sxs-lookup"><span data-stu-id="69cac-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="69cac-156">按右鍵並選擇**7-Zip -> 提取檔...**</span><span class="sxs-lookup"><span data-stu-id="69cac-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="69cac-157">在 **"提取到"** 欄位中輸入**C：\bin。**</span><span class="sxs-lookup"><span data-stu-id="69cac-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="69cac-158">取消選中 **"提取到**欄位"下的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="69cac-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="69cac-159">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69cac-159">Select **OK**.</span></span>

![安裝 .NET 火花](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="69cac-161">6. 安裝 WinUtils（僅限 Windows）</span><span class="sxs-lookup"><span data-stu-id="69cac-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="69cac-162">阿帕奇火花的 .NET 要求與阿帕奇火花一起安裝 WinUtils。</span><span class="sxs-lookup"><span data-stu-id="69cac-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="69cac-163">[下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="69cac-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="69cac-164">然後，將 WinUtils 複製到**C：\bin_spark-2.4.1-bin hadoop2.7\bin**。</span><span class="sxs-lookup"><span data-stu-id="69cac-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="69cac-165">如果您使用的是其他版本的 Hadoop（在 Spark 安裝資料夾名稱的末尾帶有批號，請選擇與您的 Hadoop 版本相容的[WinUtils 版本](https://github.com/steveloughran/winutils)。</span><span class="sxs-lookup"><span data-stu-id="69cac-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="69cac-166">7. 設置DOTNET_WORKER_DIR並檢查依賴項</span><span class="sxs-lookup"><span data-stu-id="69cac-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="69cac-167">運行以下命令之一以設置`DOTNET_WORKER_DIR`環境變數，.NET 應用使用該變數查找阿帕奇 Spark 的 .NET。</span><span class="sxs-lookup"><span data-stu-id="69cac-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="69cac-168">在**Windows**上，創建新[的環境變數](https://www.java.com/en/download/help/path.xml)`DOTNET_WORKER_DIR`，並將其設置為下載並提取 Microsoft.Spark.Worker（例如）。 `C:\bin\Microsoft.Spark.Worker\`</span><span class="sxs-lookup"><span data-stu-id="69cac-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="69cac-169">在**MacOS**上，使用`export DOTNET_WORKER_DIR <your_path>`創建新的環境變數並將其設置為下載並提取 Microsoft.Spark.Worker 的目錄（例如 *，*/bin/Microsoft.Spark.Worker/）。\*</span><span class="sxs-lookup"><span data-stu-id="69cac-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="69cac-170">在**Ubuntu**上，創建新[的環境變數](https://help.ubuntu.com/community/EnvironmentVariables)`DOTNET_WORKER_DIR`，並將其設置為下載並提取 Microsoft.Spark.Worker 的目錄（例如 *，\/bin/Microsoft.Spark.Worker）。*</span><span class="sxs-lookup"><span data-stu-id="69cac-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="69cac-171">最後，在移動到下一節之前，`dotnet`仔細檢查`java`是否可以`mvn`從`spark-shell`命令列運行 。。"</span><span class="sxs-lookup"><span data-stu-id="69cac-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="69cac-172">撰寫適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="69cac-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="69cac-173">1. 創建主控台應用</span><span class="sxs-lookup"><span data-stu-id="69cac-173">1. Create a console app</span></span>

<span data-ttu-id="69cac-174">在命令提示符或終端中，運行以下命令以創建新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="69cac-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="69cac-175">該`dotnet`命令為您創建`new`類型`console`應用程式。</span><span class="sxs-lookup"><span data-stu-id="69cac-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="69cac-176">該`-o`參數創建一個名為*mySparkApp*的目錄，其中存儲你的應用，並將其填充到所需的檔中。</span><span class="sxs-lookup"><span data-stu-id="69cac-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="69cac-177">該`cd mySparkApp`命令將目錄更改為您剛剛創建的應用目錄。</span><span class="sxs-lookup"><span data-stu-id="69cac-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="69cac-178">2. 安裝 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="69cac-178">2. Install NuGet package</span></span>

<span data-ttu-id="69cac-179">要在應用中使用的阿帕奇 Spark 的 .NET，請安裝 Microsoft.Spark 包。</span><span class="sxs-lookup"><span data-stu-id="69cac-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="69cac-180">在命令提示符或終端中，運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="69cac-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="69cac-181">3. 對應用進行編碼</span><span class="sxs-lookup"><span data-stu-id="69cac-181">3. Code your app</span></span>

<span data-ttu-id="69cac-182">打開 Visual Studio 代碼或任何文字編輯器中的*Program.cs，* 並將所有代碼替換為以下內容：</span><span class="sxs-lookup"><span data-stu-id="69cac-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="69cac-183">4. 創建並添加資料檔案</span><span class="sxs-lookup"><span data-stu-id="69cac-183">4. Create and add a data file</span></span>

<span data-ttu-id="69cac-184">打開命令提示符或終端並導航到應用資料夾。</span><span class="sxs-lookup"><span data-stu-id="69cac-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="69cac-185">你的應用處理包含文本行的檔。</span><span class="sxs-lookup"><span data-stu-id="69cac-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="69cac-186">在*mySparkApp*目錄中創建*輸入.txt*檔，其中包含以下文本：</span><span class="sxs-lookup"><span data-stu-id="69cac-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="69cac-187">執行適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="69cac-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="69cac-188">運行以下命令來生成應用程式：</span><span class="sxs-lookup"><span data-stu-id="69cac-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="69cac-189">運行以下命令以提交應用程式以在 Apache Spark 上運行：</span><span class="sxs-lookup"><span data-stu-id="69cac-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="69cac-190">此命令假定您已下載 Apache Spark 並將其添加到您的 PATH 環境變數，以便能夠使用`spark-submit`。</span><span class="sxs-lookup"><span data-stu-id="69cac-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="69cac-191">否則，您必須使用完整路徑（例如 *，C：\bin_apache-spark_bin_spark-提交*或 *_/spark/bin/spark 提交*）。</span><span class="sxs-lookup"><span data-stu-id="69cac-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="69cac-192">應用運行時 *，input.txt*檔的字計數資料將寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="69cac-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="69cac-193">恭喜！</span><span class="sxs-lookup"><span data-stu-id="69cac-193">Congratulations!</span></span> <span data-ttu-id="69cac-194">您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="69cac-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="69cac-195">後續步驟</span><span class="sxs-lookup"><span data-stu-id="69cac-195">Next steps</span></span>

<span data-ttu-id="69cac-196">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="69cac-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="69cac-197">為適用於 Apache Spark 的 .NET 準備您的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="69cac-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="69cac-198">為 Apache Spark 應用程式編寫您的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="69cac-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="69cac-199">為 Apache Spark 應用程式構建並運行您的簡單 .NET</span><span class="sxs-lookup"><span data-stu-id="69cac-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="69cac-200">要查看解釋上述步驟的視頻，請查看 Apache Spark [101 視頻系列的 .NET。](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)</span><span class="sxs-lookup"><span data-stu-id="69cac-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="69cac-201">若要深入了解，請查看資源頁面。</span><span class="sxs-lookup"><span data-stu-id="69cac-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="69cac-202">適用於 Apache Spark 的 .NET 資源</span><span class="sxs-lookup"><span data-stu-id="69cac-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
