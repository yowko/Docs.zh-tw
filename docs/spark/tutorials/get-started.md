---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows、macOS 和 Ubuntu 上使用 .NET Core 執行適用于 Apache Spark 應用程式的 .NET。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: d4f44d095fffdfa05b82516cfe79700f9e239110
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955404"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="a79a1-103">教學課程：開始使用 .NET 進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a79a1-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="a79a1-104">本教學課程會教您如何在 Windows、macOS 和 Ubuntu 上使用 .NET Core 執行 Apache Spark 應用程式的 .NET。</span><span class="sxs-lookup"><span data-stu-id="a79a1-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, macOS, and Ubuntu.</span></span>

<span data-ttu-id="a79a1-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="a79a1-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a79a1-106">準備適用于 .NET 的環境以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a79a1-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="a79a1-107">為 Apache Spark 應用程式撰寫您的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="a79a1-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a79a1-108">為 Apache Spark 應用程式建立並執行您的 .NET</span><span class="sxs-lookup"><span data-stu-id="a79a1-108">Build and run your .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="a79a1-109">準備您的環境</span><span class="sxs-lookup"><span data-stu-id="a79a1-109">Prepare your environment</span></span>

<span data-ttu-id="a79a1-110">在開始撰寫您的應用程式之前，您必須先設定一些必要條件的相依性。</span><span class="sxs-lookup"><span data-stu-id="a79a1-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="a79a1-111">如果您可以 `dotnet` `java` `spark-shell` 從命令列環境執行，則您的環境已備妥，您可以跳到下一節。</span><span class="sxs-lookup"><span data-stu-id="a79a1-111">If you can run `dotnet`, `java`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="a79a1-112">如果您無法執行任何或所有命令，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a79a1-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="a79a1-113">1. 安裝 .NET</span><span class="sxs-lookup"><span data-stu-id="a79a1-113">1. Install .NET</span></span>

<span data-ttu-id="a79a1-114">若要開始建立 .NET 應用程式，您必須下載並安裝 .NET SDK (軟體發展工具組) 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="a79a1-115">下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。</span><span class="sxs-lookup"><span data-stu-id="a79a1-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="a79a1-116">安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。</span><span class="sxs-lookup"><span data-stu-id="a79a1-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="a79a1-117">安裝 .NET Core SDK 之後，請開啟新的命令提示字元或終端機，然後執行 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="a79a1-118">如果命令執行並印出如何使用 dotnet 的相關資訊，則可以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a79a1-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="a79a1-119">如果您收到 `'dotnet' is not recognized as an internal or external command` 錯誤，請務必先開啟 **新** 的命令提示字元或終端機，然後再執行命令。</span><span class="sxs-lookup"><span data-stu-id="a79a1-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="a79a1-120">2. 安裝 JAVA</span><span class="sxs-lookup"><span data-stu-id="a79a1-120">2. Install Java</span></span>

<span data-ttu-id="a79a1-121">安裝適用于 Windows 和 macOS 的 [JAVA 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) ，或適用于 Ubuntu 的 [OpenJDK 8](https://openjdk.java.net/install/) 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and macOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="a79a1-122">為您的作業系統選取適當版本。</span><span class="sxs-lookup"><span data-stu-id="a79a1-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="a79a1-123">例如，選取 Windows x64 電腦的 **jdk-8u201-windows-x64.exe** (如下所示) 或 **jdk-8u231-macosx-x64. dmg** for macOS。</span><span class="sxs-lookup"><span data-stu-id="a79a1-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for macOS.</span></span> <span data-ttu-id="a79a1-124">然後，使用命令 `java` 來確認安裝。</span><span class="sxs-lookup"><span data-stu-id="a79a1-124">Then, use the command `java` to verify the installation.</span></span>

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="a79a1-126">3. 安裝壓縮軟體</span><span class="sxs-lookup"><span data-stu-id="a79a1-126">3. Install compression software</span></span>

<span data-ttu-id="a79a1-127">Apache Spark 會下載為壓縮的 tgz 檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="a79a1-128">使用類似 [7-Zip](https://www.7-zip.org/) 或 [WinZip](https://www.winzip.com/)的解壓縮程式來解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="a79a1-129">4. 安裝 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a79a1-129">4. Install Apache Spark</span></span>

<span data-ttu-id="a79a1-130">[下載並安裝 Apache Spark](https://spark.apache.org/downloads.html)。</span><span class="sxs-lookup"><span data-stu-id="a79a1-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="a79a1-131">您必須從 2.3. \* 或2.4.0、2.4.1、2.4.3 或2.4.4 版本中選取， ( .NET for Apache Spark 與 Apache Spark) 的其他版本不相容。</span><span class="sxs-lookup"><span data-stu-id="a79a1-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="a79a1-132">下列步驟中使用的命令假設您已 [下載並安裝 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。</span><span class="sxs-lookup"><span data-stu-id="a79a1-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="a79a1-133">如果您想要使用不同的版本，請將 **2.4.1** 取代為適當的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a79a1-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="a79a1-134">然後，將 **tar** 檔案和 Apache Spark 檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="a79a1-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="a79a1-135">若要將嵌套的 **tar** 檔案解壓縮：</span><span class="sxs-lookup"><span data-stu-id="a79a1-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="a79a1-136">找出您下載的 **spark-2.4.1-bin-hadoop 2.7. tgz** 檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="a79a1-137">以滑鼠右鍵按一下檔案，然後選取 [ **7-Zip-> 解壓縮到這裡**]。</span><span class="sxs-lookup"><span data-stu-id="a79a1-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="a79a1-138">**spark-2.4.1-bin-hadoop 2.7. tar** 會與您下載的 **tgz** 檔案一起建立。</span><span class="sxs-lookup"><span data-stu-id="a79a1-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="a79a1-139">解壓縮 Apache Spark 檔案：</span><span class="sxs-lookup"><span data-stu-id="a79a1-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="a79a1-140">以滑鼠右鍵按一下 [ **spark-2.4.1-bin-hadoop 2.7** ]，然後選取 [ **7-Zip-> 解壓縮檔案 ...** ]</span><span class="sxs-lookup"><span data-stu-id="a79a1-140">Right-click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="a79a1-141">在 [**解壓縮至**] 欄位中輸入**C:\bin** 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="a79a1-142">取消核 **取 [解壓縮至** ] 欄位下方的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a79a1-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="a79a1-143">選取 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a79a1-143">Select **OK**.</span></span>
* <span data-ttu-id="a79a1-144">Apache Spark 檔案會解壓縮至 C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="a79a1-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![安裝 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="a79a1-146">執行下列命令以設定用來尋找 Apache Spark 的環境變數。</span><span class="sxs-lookup"><span data-stu-id="a79a1-146">Run the following commands to set the environment variables used to locate Apache Spark.</span></span> <span data-ttu-id="a79a1-147">在 Windows 上，請務必在系統管理員模式中執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a79a1-147">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="a79a1-148">Windows</span><span class="sxs-lookup"><span data-stu-id="a79a1-148">Windows</span></span>](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin"
```

#### <a name="maclinux"></a>[<span data-ttu-id="a79a1-149">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="a79a1-149">Mac/Linux</span></span>](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

<span data-ttu-id="a79a1-150">當您安裝所有專案並設定環境變數之後，請開啟 **新** 的命令提示字元或終端機，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a79a1-150">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

```text
spark-submit --version
```

<span data-ttu-id="a79a1-151">如果命令執行並列印版本資訊，您可以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a79a1-151">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="a79a1-152">如果您收到 `'spark-submit' is not recognized as an internal or external command` 錯誤，請確定您已開啟 **新** 的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a79a1-152">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="a79a1-153">5. 安裝適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="a79a1-153">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="a79a1-154">從 .NET 下載 Apache Spark GitHub 的[。](https://github.com/dotnet/spark/releases)</span><span class="sxs-lookup"><span data-stu-id="a79a1-154">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="a79a1-155">例如，如果您是在 Windows 電腦上，並打算使用 .NET Core，請 [下載 windows x64 netcoreapp 3.1 版本](https://github.com/dotnet/spark/releases)。</span><span class="sxs-lookup"><span data-stu-id="a79a1-155">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases).</span></span>

<span data-ttu-id="a79a1-156">若要將 Microsoft. 背景工作角色解壓縮：</span><span class="sxs-lookup"><span data-stu-id="a79a1-156">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="a79a1-157">找出您下載的 **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** 檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-157">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="a79a1-158">以滑鼠右鍵按一下並選取 [ **7-Zip-> 解壓縮檔**案 ...]。</span><span class="sxs-lookup"><span data-stu-id="a79a1-158">Right-click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="a79a1-159">在 [**解壓縮至**] 欄位中輸入**C:\bin** 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-159">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="a79a1-160">取消核 **取 [解壓縮至** ] 欄位下方的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a79a1-160">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="a79a1-161">選取 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a79a1-161">Select **OK**.</span></span>

![安裝 .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="a79a1-163">6. 僅將 Winutils.exe 安裝 (Windows) </span><span class="sxs-lookup"><span data-stu-id="a79a1-163">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="a79a1-164">Apache Spark 的 .NET 需要與 Apache Spark 一起安裝 Winutils.exe。</span><span class="sxs-lookup"><span data-stu-id="a79a1-164">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="a79a1-165">[下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。</span><span class="sxs-lookup"><span data-stu-id="a79a1-165">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="a79a1-166">然後，將 Winutils.exe 複製到 **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**。</span><span class="sxs-lookup"><span data-stu-id="a79a1-166">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="a79a1-167">如果您使用的是不同版本的 Hadoop （在 Spark 安裝資料夾名稱的結尾加上批註），請選取與您的 Hadoop 版本相容的 [winutils.exe 版本](https://github.com/steveloughran/winutils) 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-167">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="a79a1-168">7. 設定 DOTNET_WORKER_DIR 並檢查相依性</span><span class="sxs-lookup"><span data-stu-id="a79a1-168">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="a79a1-169">執行下列其中一個命令來設定 `DOTNET_WORKER_DIR` 環境變數，.net 應用程式會使用它來尋找 Apache Spark 的 .net。</span><span class="sxs-lookup"><span data-stu-id="a79a1-169">Run one of the following commands to set the `DOTNET_WORKER_DIR` environment variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span> <span data-ttu-id="a79a1-170">請務必將取代為 `<PATH-DOTNET_WORKER_DIR>` 您下載並解壓縮的目錄 `Microsoft.Spark.Worker` 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-170">Make sure to replace `<PATH-DOTNET_WORKER_DIR>` with the directory where you downloaded and extracted the `Microsoft.Spark.Worker`.</span></span> <span data-ttu-id="a79a1-171">在 Windows 上，請務必在系統管理員模式中執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a79a1-171">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="a79a1-172">Windows</span><span class="sxs-lookup"><span data-stu-id="a79a1-172">Windows</span></span>](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[<span data-ttu-id="a79a1-173">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="a79a1-173">Mac/Linux</span></span>](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

<span data-ttu-id="a79a1-174">最後，再次檢查您可以 `dotnet` `java` `spark-shell` 從命令列執行，然後再移至下一節。</span><span class="sxs-lookup"><span data-stu-id="a79a1-174">Finally, double-check that you can run `dotnet`, `java`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="a79a1-175">撰寫適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="a79a1-175">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="a79a1-176">1. 建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a79a1-176">1. Create a console app</span></span>

<span data-ttu-id="a79a1-177">在您的命令提示字元或終端機中執行下列命令，以建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="a79a1-177">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

<span data-ttu-id="a79a1-178">此 `dotnet` 命令 `new` 會為您建立類型的應用程式 `console` 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-178">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="a79a1-179">`-o`參數會建立名為*MySparkApp*的目錄，您的應用程式會儲存在此目錄中，並填入必要的檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-179">The `-o` parameter creates a directory named *MySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a79a1-180">此 `cd MySparkApp` 命令會將目錄變更為您所建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="a79a1-180">The `cd MySparkApp` command changes the directory to the app directory you created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="a79a1-181">2. 安裝 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="a79a1-181">2. Install NuGet package</span></span>

<span data-ttu-id="a79a1-182">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="a79a1-182">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="a79a1-183">在您的命令提示字元或終端機中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a79a1-183">In your command prompt or terminal, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> <span data-ttu-id="a79a1-184">除非另有指定，否則本教學課程會使用最新版本的 `Microsoft.Spark` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a79a1-184">This tutorial uses the latest version of the `Microsoft.Spark` NuGet package unless otherwise specified.</span></span>

### <a name="3-write-your-app"></a><span data-ttu-id="a79a1-185">3. 撰寫您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a79a1-185">3. Write your app</span></span>

<span data-ttu-id="a79a1-186">在 Visual Studio Code 或任何文字編輯器中開啟 *Program.cs* ，並以下列程式碼取代所有程式碼：</span><span class="sxs-lookup"><span data-stu-id="a79a1-186">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;
using static Microsoft.Spark.Sql.Functions;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create Spark session
            SparkSession spark =
                SparkSession
                    .Builder()
                    .AppName("word_count_sample")
                    .GetOrCreate();

            // Create initial DataFrame
            string filePath = args[0];
            DataFrame dataFrame = spark.Read().Text(filePath);

            //Count words
            DataFrame words =
                dataFrame
                    .Select(Split(Col("value")," ").Alias("words"))
                    .Select(Explode(Col("words")).Alias("word"))
                    .GroupBy("word")
                    .Count()
                    .OrderBy(Col("count").Desc());

            // Display results
            words.Show();

            // Stop Spark session
            spark.Stop();
        }
    }
}
```

<span data-ttu-id="a79a1-187">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) 是 Apache Spark 應用程式的進入點，可管理應用程式的內容和資訊。</span><span class="sxs-lookup"><span data-stu-id="a79a1-187">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) is the entrypoint of Apache Spark applications, which manages the context and information of your application.</span></span> <span data-ttu-id="a79a1-188">使用 [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) 方法時，所指定之檔案中的文字資料 `filePath` 會讀入 [資料框架](xref:Microsoft.Spark.Sql.DataFrame)中。</span><span class="sxs-lookup"><span data-stu-id="a79a1-188">Using the [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) method, the text data from the file specified by the `filePath` is read into a [DataFrame](xref:Microsoft.Spark.Sql.DataFrame).</span></span> <span data-ttu-id="a79a1-189">資料框架是一種將資料組織成一組命名的資料行的方式。</span><span class="sxs-lookup"><span data-stu-id="a79a1-189">A DataFrame is a way of organizing data into a set of named columns.</span></span> <span data-ttu-id="a79a1-190">然後，套用一連串的轉換來分割檔案中的句子、將每個字組分組、計算它們，然後以遞減順序排序它們。</span><span class="sxs-lookup"><span data-stu-id="a79a1-190">Then, a series of transformations is applied to split the sentences in the file, group each of the words, count them and order them in descending order.</span></span> <span data-ttu-id="a79a1-191">這些作業的結果會儲存在另一個資料框架中。</span><span class="sxs-lookup"><span data-stu-id="a79a1-191">The result of these operations is stored in another DataFrame.</span></span> <span data-ttu-id="a79a1-192">請注意，此時不會執行任何作業，因為 .NET for Apache Spark 會延遲評估資料。</span><span class="sxs-lookup"><span data-stu-id="a79a1-192">Note that at this point, no operations have taken place because .NET for Apache Spark lazily evaluates the data.</span></span> <span data-ttu-id="a79a1-193">在呼叫 [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) 方法之前，它並不會顯示已 `words` 轉換資料框架至主控台的內容，以執行上述各行中定義的作業。</span><span class="sxs-lookup"><span data-stu-id="a79a1-193">It's not until the [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) method is called to display the contents of the `words` transformed DataFrame to the console that the operations defined in the lines above execute.</span></span> <span data-ttu-id="a79a1-194">一旦不再需要 Spark 會話，請使用 [stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) 方法停止您的會話。</span><span class="sxs-lookup"><span data-stu-id="a79a1-194">Once you no longer need the Spark session, use the [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) method to stop your session.</span></span>

### <a name="4-create-data-file"></a><span data-ttu-id="a79a1-195">4. 建立資料檔案</span><span class="sxs-lookup"><span data-stu-id="a79a1-195">4. Create data file</span></span>

<span data-ttu-id="a79a1-196">您的應用程式會處理包含文字行的檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-196">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="a79a1-197">在*MySparkApp*目錄中建立名為*input.txt* file 的檔案，其中包含下列文字：</span><span class="sxs-lookup"><span data-stu-id="a79a1-197">Create a file called *input.txt* file in your *MySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

<span data-ttu-id="a79a1-198">儲存變更並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="a79a1-198">Save the changes and close the file.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="a79a1-199">執行適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="a79a1-199">Run your .NET for Apache Spark app</span></span>

<span data-ttu-id="a79a1-200">執行下列命令以建立您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="a79a1-200">Run the following command to build your application:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a79a1-201">流覽至您的組建輸出目錄，然後使用 `spark-submit` 命令來提交要在 Apache Spark 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a79a1-201">Navigate to your build output directory and use the `spark-submit` command to submit your application to run on Apache Spark.</span></span> <span data-ttu-id="a79a1-202">請務必以  `<version>` 您的 .net 背景工作版本取代，並以 `<path-of-input.txt>` 您的 *input.txt* 檔案的路徑取代。</span><span class="sxs-lookup"><span data-stu-id="a79a1-202">Make sure to replace  `<version>` with the version of your .NET worker and `<path-of-input.txt>` with the path of your *input.txt* file is stored.</span></span>

### <a name="windows"></a>[<span data-ttu-id="a79a1-203">Windows</span><span class="sxs-lookup"><span data-stu-id="a79a1-203">Windows</span></span>](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-2.4.x-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[<span data-ttu-id="a79a1-204">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="a79a1-204">Mac/Linux</span></span>](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-2.4.x-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> <span data-ttu-id="a79a1-205">此命令假設您已下載 Apache Spark，並將其新增至 PATH 環境變數，以便能夠使用 `spark-submit` 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-205">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="a79a1-206">否則，您必須使用完整路徑 (例如 *C:\bin\apache-spark\bin\spark-submit* 或 *~/spark/bin/spark-submit*) 。</span><span class="sxs-lookup"><span data-stu-id="a79a1-206">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

<span data-ttu-id="a79a1-207">當您的應用程式執行時，會將 *input.txt* 檔案的字數統計資料寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="a79a1-207">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

```console
+------+-----+
|  word|count|
+------+-----+
|  .NET|    3|
|Apache|    2|
|   app|    2|
|  This|    2|
| Spark|    2|
| World|    1|
|counts|    1|
|   for|    1|
| words|    1|
|  with|    1|
| Hello|    1|
|  uses|    1|
+------+-----+
```

<span data-ttu-id="a79a1-208">恭喜！</span><span class="sxs-lookup"><span data-stu-id="a79a1-208">Congratulations!</span></span> <span data-ttu-id="a79a1-209">您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a79a1-209">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a79a1-210">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a79a1-210">Next steps</span></span>

<span data-ttu-id="a79a1-211">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="a79a1-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a79a1-212">準備適用于 .NET 的環境以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a79a1-212">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="a79a1-213">為 Apache Spark 應用程式撰寫您的第一個 .NET</span><span class="sxs-lookup"><span data-stu-id="a79a1-213">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a79a1-214">為 Apache Spark 應用程式建立並執行您的 .NET</span><span class="sxs-lookup"><span data-stu-id="a79a1-214">Build and run your .NET for Apache Spark application</span></span>

<span data-ttu-id="a79a1-215">若要查看說明上述步驟的影片，請參閱 [適用于 Apache Spark 101 影片系列的 .net](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。</span><span class="sxs-lookup"><span data-stu-id="a79a1-215">To see a video explaining the steps above, check out the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="a79a1-216">若要深入了解，請查看資源頁面。</span><span class="sxs-lookup"><span data-stu-id="a79a1-216">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a79a1-217">適用於 Apache Spark 的 .NET 資源</span><span class="sxs-lookup"><span data-stu-id="a79a1-217">.NET for Apache Spark Resources</span></span>](../resources/index.md)
