---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows、MacOS 和 Ubuntu 上使用 .NET Core 來執行適用于 Apache Spark 應用程式的 .NET。
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: be150bcef0029f69136e21c35791c863220af244
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617648"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="ca1c0-103">教學課程：開始使用適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="ca1c0-104">本教學課程會教您如何在 Windows、MacOS 和 Ubuntu 上使用 .NET Core 來執行適用于 Apache Spark 應用程式的 .NET。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="ca1c0-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="ca1c0-106">準備適用于 .NET 的環境以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ca1c0-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="ca1c0-107">撰寫 Apache Spark 應用程式的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="ca1c0-108">為 Apache Spark 應用程式建立及執行您的簡單 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-108">Build and run your simple .NET for Apache Spark application</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="ca1c0-109">準備您的環境</span><span class="sxs-lookup"><span data-stu-id="ca1c0-109">Prepare your environment</span></span>

<span data-ttu-id="ca1c0-110">開始撰寫應用程式之前，您必須先設定一些必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="ca1c0-111">如果您可以 `dotnet` `java` `mvn` `spark-shell` 從命令列環境執行、、，則您的環境已準備就緒，您可以跳到下一節。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="ca1c0-112">如果您無法執行任何或所有的命令，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="ca1c0-113">1. 安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-113">1. Install .NET</span></span>

<span data-ttu-id="ca1c0-114">若要開始建立 .NET 應用程式，您必須下載並安裝 .NET SDK （軟體發展工具組）。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="ca1c0-115">下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="ca1c0-116">安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="ca1c0-117">安裝 .NET Core SDK 之後，請開啟新的命令提示字元或終端機，然後執行 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="ca1c0-118">如果命令執行並印出有關如何使用 dotnet 的資訊，可以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="ca1c0-119">如果您收到 `'dotnet' is not recognized as an internal or external command` 錯誤，請確定您在執行命令之前，已開啟**新**的命令提示字元或終端機。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="ca1c0-120">2. 安裝 JAVA</span><span class="sxs-lookup"><span data-stu-id="ca1c0-120">2. Install Java</span></span>

<span data-ttu-id="ca1c0-121">安裝適用于 Windows 和 MacOS 的[JAVA 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) ，或適用于 Ubuntu 的[OpenJDK 8](https://openjdk.java.net/install/) 。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="ca1c0-122">為您的作業系統選取適當版本。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="ca1c0-123">例如，選取適用于 Windows x64 電腦的**jdk-8u201-windows-x64.exe** （如下所示）或**jdk-8u231-macosx-x64. dmg** for MacOS。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="ca1c0-124">然後，使用命令 `java` 來確認安裝。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-124">Then, use the command `java` to verify the installation.</span></span>

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="ca1c0-126">3. 安裝壓縮軟體</span><span class="sxs-lookup"><span data-stu-id="ca1c0-126">3. Install compression software</span></span>

<span data-ttu-id="ca1c0-127">Apache Spark 會下載為 tgz 檔案。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="ca1c0-128">使用類似[7-Zip](https://www.7-zip.org/)或[WinZip](https://www.winzip.com/)的抽取程式來解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="ca1c0-129">4. 安裝 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ca1c0-129">4. Install Apache Spark</span></span>

<span data-ttu-id="ca1c0-130">[下載並安裝 Apache Spark](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="ca1c0-131">您必須選取版本 2.3. \* 或2.4.0、2.4.1、2.4.3 或2.4.4 （適用于 Apache Spark 的 .NET 與 Apache Spark 的其他版本不相容）。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="ca1c0-132">下列步驟中使用的命令假設您已[下載並安裝 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="ca1c0-133">如果您想要使用不同的版本，請將**2.4.1**取代為適當的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="ca1c0-134">然後，將**tar**檔案和 Apache Spark 檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="ca1c0-135">若要解壓縮嵌套的**tar**檔案：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="ca1c0-136">找出您已下載的**spark-2.4.1-bin-hadoop 2.7. tgz**檔案。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="ca1c0-137">以滑鼠右鍵按一下檔案，然後選取 [ **7-Zip-> 解壓縮到這裡**]。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="ca1c0-138">**spark-2.4.1-bin-hadoop 2.7. tar**會連同您下載的**tgz**檔案一起建立。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="ca1c0-139">若要解壓縮 Apache Spark 檔案：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="ca1c0-140">以滑鼠右鍵按一下 [ **spark-2.4.1-bin-hadoop 2.7. tar** ]，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]</span><span class="sxs-lookup"><span data-stu-id="ca1c0-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="ca1c0-141">在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="ca1c0-142">取消核**取 [解壓縮至**] 欄位下方的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="ca1c0-143">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-143">Select **OK**.</span></span>
* <span data-ttu-id="ca1c0-144">Apache Spark 檔案會解壓縮至 C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="ca1c0-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![安裝 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="ca1c0-146">執行下列命令，設定用來在**Windows**上尋找 Apache Spark 的環境變數：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="ca1c0-147">執行下列命令，設定用來在**MacOS**和**Ubuntu**上尋找 Apache Spark 的環境變數：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="ca1c0-148">安裝所有專案並設定您的環境變數之後，請開啟**新**的命令提示字元或終端機，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="ca1c0-149">如果命令執行並列印版本資訊，您可以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="ca1c0-150">如果您收到 `'spark-submit' is not recognized as an internal or external command` 錯誤，請確定您已開啟**新**的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="ca1c0-151">5. 安裝適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="ca1c0-152">從適用于 Apache Spark GitHub 的 .NET 下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases)版本。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="ca1c0-153">例如，如果您是在 Windows 電腦上，並打算使用 .NET Core，請[下載 windows x64 netcoreapp 3.1 版](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="ca1c0-154">若要解壓縮 Microsoft. Spark. Worker：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="ca1c0-155">找出您下載的**Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip**檔案。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="ca1c0-156">按一下滑鼠右鍵，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="ca1c0-157">在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="ca1c0-158">取消核**取 [解壓縮至**] 欄位下方的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="ca1c0-159">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-159">Select **OK**.</span></span>

![安裝 .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="ca1c0-161">6. 安裝 Winutils.exe （僅限 Windows）</span><span class="sxs-lookup"><span data-stu-id="ca1c0-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="ca1c0-162">適用于 Apache Spark 的 .NET 需要與 Apache Spark 一起安裝 Winutils.exe。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="ca1c0-163">[下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="ca1c0-164">然後，將 Winutils.exe 複製到**C:\bin\spark-2.4.1-bin-hadoop2.7\bin**。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="ca1c0-165">如果您使用的是不同版本的 Hadoop （在 Spark 安裝資料夾名稱的結尾加上批註），請選取與您的 Hadoop 版本相容的[winutils.exe 版本](https://github.com/steveloughran/winutils)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="ca1c0-166">7. 設定 DOTNET_WORKER_DIR 並檢查相依性</span><span class="sxs-lookup"><span data-stu-id="ca1c0-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="ca1c0-167">執行下列其中一個命令來設定 `DOTNET_WORKER_DIR` 環境變數，以供 .net 應用程式用來尋找 Apache Spark 的 .net。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="ca1c0-168">在**Windows**上，建立[新的環境變數](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` ，並將它設定為您下載並解壓縮的目錄（例如， `C:\bin\Microsoft.Spark.Worker\` ）。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="ca1c0-169">在**MacOS**上，使用建立新的環境變數 `export DOTNET_WORKER_DIR <your_path>` ，並將它設定為您下載並解壓縮的目錄（例如 *~/bin/Microsoft.Spark.Worker/*）。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="ca1c0-170">在**Ubuntu**上，建立[新的環境變數](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` ，並將它設定為您下載並解壓縮的目錄（例如 *~/bin/Microsoft.Spark.Worker*）。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="ca1c0-171">最後，再次檢查您是否可以 `dotnet` `java` 從命令列執行、、 `mvn` ， `spark-shell` 然後再移至下一節。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="ca1c0-172">撰寫適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca1c0-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="ca1c0-173">1. 建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ca1c0-173">1. Create a console app</span></span>

<span data-ttu-id="ca1c0-174">在您的命令提示字元或終端機中，執行下列命令來建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="ca1c0-175">`dotnet`命令 `new` 會為您建立類型的應用程式 `console` 。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="ca1c0-176">`-o`參數會建立名為*mySparkApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="ca1c0-177">此 `cd mySparkApp` 命令會將目錄變更為您剛才建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="ca1c0-178">2. 安裝 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="ca1c0-178">2. Install NuGet package</span></span>

<span data-ttu-id="ca1c0-179">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="ca1c0-180">在您的命令提示字元或終端機中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="ca1c0-181">3. 編碼您的應用程式</span><span class="sxs-lookup"><span data-stu-id="ca1c0-181">3. Code your app</span></span>

<span data-ttu-id="ca1c0-182">在 Visual Studio Code 或任何文字編輯器中開啟*Program.cs* ，並將所有程式碼取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

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

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="ca1c0-183">4. 建立和新增資料檔案</span><span class="sxs-lookup"><span data-stu-id="ca1c0-183">4. Create and add a data file</span></span>

<span data-ttu-id="ca1c0-184">開啟命令提示字元或終端機，並流覽至您的應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="ca1c0-185">您的應用程式會處理包含文字行的檔案。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="ca1c0-186">在*mySparkApp*目錄中建立*input.txt*檔案，其中包含下列文字：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="ca1c0-187">執行適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="ca1c0-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="ca1c0-188">執行下列命令來建立您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="ca1c0-189">執行下列命令，以提交要在 Apache Spark 上執行的應用程式：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="ca1c0-190">此命令假設您已下載 Apache Spark，並將它新增至您的 PATH 環境變數，以便能夠使用 `spark-submit` 。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="ca1c0-191">否則，您必須使用完整路徑（例如， *C:\bin\apache-spark\bin\spark-submit*或 *~/spark/bin/spark-submit*）。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="ca1c0-192">當您的應用程式執行時，會將*input.txt*檔案的字數統計資料寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="ca1c0-193">恭喜！</span><span class="sxs-lookup"><span data-stu-id="ca1c0-193">Congratulations!</span></span> <span data-ttu-id="ca1c0-194">您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ca1c0-195">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ca1c0-195">Next steps</span></span>

<span data-ttu-id="ca1c0-196">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="ca1c0-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="ca1c0-197">為適用於 Apache Spark 的 .NET 準備您的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="ca1c0-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="ca1c0-198">撰寫 Apache Spark 應用程式的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="ca1c0-199">為 Apache Spark 應用程式建立及執行您的簡單 .NET</span><span class="sxs-lookup"><span data-stu-id="ca1c0-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="ca1c0-200">若要觀看說明上述步驟的影片，請參閱[適用于 Apache Spark 101 的 .net 影片系列](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="ca1c0-201">若要深入了解，請查看資源頁面。</span><span class="sxs-lookup"><span data-stu-id="ca1c0-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ca1c0-202">適用於 Apache Spark 的 .NET 資源</span><span class="sxs-lookup"><span data-stu-id="ca1c0-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
