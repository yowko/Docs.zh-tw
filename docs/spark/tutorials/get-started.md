---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows 上使用 .NET Core 執行適用於 Apache Spark 的 .NET 應用程式。
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743210"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="a9b5a-103">教學課程：開始使用適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="a9b5a-104">本教學課程將指導您如何在 Windows 上使用 .NET Core，執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="a9b5a-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a9b5a-106">為適用於 Apache Spark 的 .NET 準備您的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="a9b5a-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="a9b5a-107">撰寫 Apache Spark 應用程式的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a9b5a-108">為 Apache Spark 應用程式建立及執行您的簡單 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="a9b5a-109">準備您的環境</span><span class="sxs-lookup"><span data-stu-id="a9b5a-109">Prepare your environment</span></span>

<span data-ttu-id="a9b5a-110">開始撰寫應用程式之前，您必須先設定一些必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="a9b5a-111">如果您可以從命令列環境執行 `dotnet`、`java`、`mvn``spark-shell`，則您的環境已準備就緒，您可以跳到下一節。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="a9b5a-112">如果您無法執行任何或所有的命令，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="a9b5a-113">1. 安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-113">1. Install .NET</span></span>

<span data-ttu-id="a9b5a-114">若要開始建立 .NET 應用程式，您必須下載並安裝 .NET SDK （軟體發展工具組）。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="a9b5a-115">下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="a9b5a-116">安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="a9b5a-117">安裝 .NET Core SDK 之後，請開啟新的命令提示字元，然後執行 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-117">Once you've installed the .NET Core SDK, open a new command prompt and run `dotnet`.</span></span>

<span data-ttu-id="a9b5a-118">如果命令執行並印出有關如何使用 dotnet 的資訊，可以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="a9b5a-119">如果您收到 `'dotnet' is not recognized as an internal or external command` 錯誤，請確定您在執行命令之前，已開啟**新**的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="a9b5a-120">2. 安裝 JAVA</span><span class="sxs-lookup"><span data-stu-id="a9b5a-120">2. Install Java</span></span>

<span data-ttu-id="a9b5a-121">安裝[JAVA 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

<span data-ttu-id="a9b5a-122">為您的作業系統選取適當版本。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="a9b5a-123">例如，為 Windows x64 電腦選取 **jdk-8u201-windows-x64.exe**。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span> <span data-ttu-id="a9b5a-124">然後，使用命令 `java` 來確認安裝。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-124">Then, use the command `java` to verify the installation.</span></span>

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a><span data-ttu-id="a9b5a-126">3. 安裝 7-zip</span><span class="sxs-lookup"><span data-stu-id="a9b5a-126">3. Install 7-zip</span></span>

<span data-ttu-id="a9b5a-127">Apache Spark 會下載為 tgz 檔案。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="a9b5a-128">使用類似 7-zip 的抽取程式來解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-128">Use an extraction program, like 7-zip, to extract the file.</span></span>

* <span data-ttu-id="a9b5a-129">流覽[7-Zip 下載](https://www.7-zip.org/)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-129">Visit [7-Zip downloads](https://www.7-zip.org/).</span></span>
* <span data-ttu-id="a9b5a-130">在頁面上的第一個表格中，根據您的作業系統選取32位 x86 或64位 x64 下載。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-130">In the first table on the page, select the 32-bit x86 or 64-bit x64 download, depending on your operating system.</span></span>
* <span data-ttu-id="a9b5a-131">當下載完成時，執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-131">When the download completes, run the installer.</span></span>

![7Zip 下載](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a><span data-ttu-id="a9b5a-133">4. 安裝 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a9b5a-133">4. Install Apache Spark</span></span>

<span data-ttu-id="a9b5a-134">[下載並安裝 Apache Spark](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-134">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="a9b5a-135">您必須選取版本 2.3. \* 或2.4.0、2.4.1、2.4.3 或2.4.4 （適用于 Apache Spark 的 .NET 與 Apache Spark 的其他版本不相容）。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-135">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="a9b5a-136">下列步驟中使用的命令假設您已[下載並安裝 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-136">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="a9b5a-137">如果您想要使用不同的版本，請將**2.4.1**取代為適當的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-137">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="a9b5a-138">然後，將**tar**檔案和 Apache Spark 檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-138">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="a9b5a-139">若要解壓縮嵌套的**tar**檔案：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-139">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="a9b5a-140">找出您已下載的**spark-2.4.1-bin-hadoop 2.7. tgz**檔案。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-140">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="a9b5a-141">以滑鼠右鍵按一下檔案，然後選取 [ **7-Zip-> 解壓縮到這裡**]。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-141">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="a9b5a-142">**spark-2.4.1-bin-hadoop 2.7. tar**會連同您下載的**tgz**檔案一起建立。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-142">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="a9b5a-143">若要解壓縮 Apache Spark 檔案：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-143">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="a9b5a-144">以滑鼠右鍵按一下 [ **spark-2.4.1-bin-hadoop 2.7. tar** ]，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]</span><span class="sxs-lookup"><span data-stu-id="a9b5a-144">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="a9b5a-145">在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-145">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="a9b5a-146">取消核**取 [解壓縮至**] 欄位下方的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-146">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="a9b5a-147">選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-147">Select **OK**.</span></span>
* <span data-ttu-id="a9b5a-148">Apache Spark 檔案會解壓縮至 C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="a9b5a-148">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![安裝 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="a9b5a-150">執行下列命令，設定用來尋找 Apache Spark 的環境變數：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-150">Run the following commands to set the environment variables used to locate Apache Spark:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="a9b5a-151">安裝所有專案並設定您的環境變數之後，請開啟**新**的命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-151">Once you've installed everything and set your environment variables, open a **new** command prompt and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="a9b5a-152">如果命令執行並列印版本資訊，您可以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-152">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="a9b5a-153">如果您收到 `'spark-submit' is not recognized as an internal or external command` 錯誤，請確定您已開啟**新**的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-153">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="a9b5a-154">5. 安裝適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-154">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="a9b5a-155">從適用于 Apache Spark GitHub 的 .NET 下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases)版本。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-155">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="a9b5a-156">例如，如果您是在 Windows 電腦上，並打算使用 .NET Core，請[下載 windows x64 netcoreapp 2.1 版](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-156">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp2.1 release](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span></span>

<span data-ttu-id="a9b5a-157">若要解壓縮 Microsoft. Spark. Worker：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-157">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="a9b5a-158">找出您下載的**netcoreapp 2.1. win-x64-0.6.0 .zip**檔案。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-158">Locate the **Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="a9b5a-159">按一下滑鼠右鍵，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-159">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="a9b5a-160">在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-160">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="a9b5a-161">取消核**取 [解壓縮至**] 欄位下方的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-161">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="a9b5a-162">選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-162">Select **OK**.</span></span>

![安裝 .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a><span data-ttu-id="a9b5a-164">6. 安裝 Winutils.exe</span><span class="sxs-lookup"><span data-stu-id="a9b5a-164">6. Install WinUtils</span></span>

<span data-ttu-id="a9b5a-165">適用于 Apache Spark 的 .NET 需要與 Apache Spark 一起安裝 Winutils.exe。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-165">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="a9b5a-166">[下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-166">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="a9b5a-167">然後，將 Winutils.exe 複製到**C:\bin\spark-2.4.1-bin-hadoop2.7\bin**。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-167">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="a9b5a-168">如果您使用的是不同版本的 Hadoop （在 Spark 安裝資料夾名稱的結尾加上批註），請選取與您的 Hadoop 版本相容的[winutils.exe 版本](https://github.com/steveloughran/winutils)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-168">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="a9b5a-169">7. 設定 DOTNET_WORKER_DIR 並檢查相依性</span><span class="sxs-lookup"><span data-stu-id="a9b5a-169">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="a9b5a-170">執行下列命令來設定 `DOTNET_WORKER_DIR` 環境變數，以供 .NET 應用程式用來找出適用于 Apache Spark 的 .NET：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-170">Run the following command to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark:</span></span>

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

<span data-ttu-id="a9b5a-171">最後，再次檢查您可以從命令列執行 `dotnet`、`java`、`mvn``spark-shell`，然後再移到下一節。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="a9b5a-172">撰寫適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="a9b5a-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="a9b5a-173">1. 建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a9b5a-173">1. Create a console app</span></span>

<span data-ttu-id="a9b5a-174">在命令提示字元中，執行下列命令以建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-174">In your command prompt, run the following commands to create a new console application:</span></span>

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="a9b5a-175">`dotnet` 命令會為您建立類型為 `console` 的 `new` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="a9b5a-176">`-o` 參數會建立名為*mySparkApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a9b5a-177">`cd mySparkApp` 命令會將目錄變更為您剛才建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="a9b5a-178">2. 安裝 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="a9b5a-178">2. Install NuGet package</span></span>

<span data-ttu-id="a9b5a-179">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="a9b5a-180">在命令提示字元中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-180">In your command prompt, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a><span data-ttu-id="a9b5a-181">3. 編碼您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a9b5a-181">3. Code your app</span></span>

<span data-ttu-id="a9b5a-182">在 Visual Studio Code 或任何文字編輯器中開啟*Program.cs* ，並將所有程式碼取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
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

### <a name="4-add-data-file"></a><span data-ttu-id="a9b5a-183">4. 加入資料檔案</span><span class="sxs-lookup"><span data-stu-id="a9b5a-183">4. Add data file</span></span>

<span data-ttu-id="a9b5a-184">您的應用程式會處理包含文字行的檔案。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-184">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="a9b5a-185">在您的*mySparkApp*目錄中建立*輸入 .txt*檔案，其中包含下列文字：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-185">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="a9b5a-186">執行適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="a9b5a-186">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="a9b5a-187">執行下列命令來建立您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-187">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="a9b5a-188">執行下列命令，以提交要在 Apache Spark 上執行的應用程式：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-188">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. <span data-ttu-id="a9b5a-189">當您的應用程式執行時，會將*輸入 .txt*檔案的字數統計資料寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-189">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="a9b5a-190">恭喜！</span><span class="sxs-lookup"><span data-stu-id="a9b5a-190">Congratulations!</span></span> <span data-ttu-id="a9b5a-191">您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-191">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a9b5a-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a9b5a-192">Next steps</span></span>

<span data-ttu-id="a9b5a-193">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="a9b5a-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a9b5a-194">為適用於 Apache Spark 的 .NET 準備您的 Windows 環境</span><span class="sxs-lookup"><span data-stu-id="a9b5a-194">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="a9b5a-195">撰寫 Apache Spark 應用程式的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-195">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a9b5a-196">為 Apache Spark 應用程式建立及執行您的簡單 .NET</span><span class="sxs-lookup"><span data-stu-id="a9b5a-196">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="a9b5a-197">若要觀看說明上述步驟的影片，請參閱[適用于 Apache Spark 101 的 .net 影片系列](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-197">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="a9b5a-198">若要深入了解，請查看資源頁面。</span><span class="sxs-lookup"><span data-stu-id="a9b5a-198">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a9b5a-199">適用於 Apache Spark 的 .NET 資源</span><span class="sxs-lookup"><span data-stu-id="a9b5a-199">.NET for Apache Spark Resources</span></span>](../resources/index.md)
