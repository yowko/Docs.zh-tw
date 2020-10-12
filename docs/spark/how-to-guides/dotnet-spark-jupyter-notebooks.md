---
title: 使用 Jupyter Notebook
titleSuffix: .NET for Apache Spark
description: '在互動式環境中使用 .NET 進行 Apache Spark，例如 Jupyter Notebook、Jupyter Lab 或 Visual Studio Code (VS Code) '
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: 38263c5ce4d1686777f33f5a9742d530eafa9d89
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955708"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a><span data-ttu-id="349e3-103">在 Jupyter 筆記本中使用 .NET 進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="349e3-103">Use .NET for Apache Spark in Jupyter notebooks</span></span>

<span data-ttu-id="349e3-104">在本文中，您將瞭解如何以互動方式，在 Jupyter Notebook 中以互動方式執行 Apache Spark 工作，並使用 .NET Interactive Visual Studio Code (VS Code) 。</span><span class="sxs-lookup"><span data-stu-id="349e3-104">In this article, you learn how to run .NET for Apache Spark jobs interactively in Jupyter Notebook and Visual Studio Code (VS Code) with .NET Interactive.</span></span>

## <a name="about-jupyter"></a><span data-ttu-id="349e3-105">關於 Jupyter</span><span class="sxs-lookup"><span data-stu-id="349e3-105">About Jupyter</span></span>

<span data-ttu-id="349e3-106">[Jupyter](https://jupyter.org/) 是開放原始碼的跨平臺運算環境，可讓使用者以互動方式原型設計和開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="349e3-106">[Jupyter](https://jupyter.org/) is an open-source, cross-platform computing environment that provides a way for users to prototype and develop applications interactively.</span></span> <span data-ttu-id="349e3-107">您可以透過各種不同的介面（例如 Jupyter Notebook、Jupyter Lab 和 VS Code）來與 Jupyter 互動。</span><span class="sxs-lookup"><span data-stu-id="349e3-107">You can interact with Jupyter through a wide variety of interfaces such as Jupyter Notebook, Jupyter Lab, and VS Code.</span></span>

<span data-ttu-id="349e3-108">在 .NET 的環境中，.net [Interactive](https://github.com/dotnet/interactive)（.net Core 通用工具）提供核心，可在互動式運算環境（例如 Jupyter Notebook）中撰寫 .net 程式碼 (c #/f # ) 。</span><span class="sxs-lookup"><span data-stu-id="349e3-108">In the context of .NET, [.NET Interactive](https://github.com/dotnet/interactive), a .NET Core global tool, provides a kernel for writing .NET code (C#/F#) in interactive computing environments such as Jupyter Notebook.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="349e3-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="349e3-109">Prerequisites</span></span>

- [<span data-ttu-id="349e3-110">.NET Core 3.1 SDK</span><span class="sxs-lookup"><span data-stu-id="349e3-110">.NET Core 3.1 SDK</span></span>](https://docs.microsoft.com/dotnet/core/install/)
- [<span data-ttu-id="349e3-111">Apache Spark</span><span class="sxs-lookup"><span data-stu-id="349e3-111">Apache Spark</span></span>](https://spark.apache.org/downloads.html)
- [<span data-ttu-id="349e3-112">Apache Spark .NET 背景工作</span><span class="sxs-lookup"><span data-stu-id="349e3-112">Apache Spark .NET Worker</span></span>](https://github.com/dotnet/spark/releases)

<span data-ttu-id="349e3-113">如需有關為 Apache Spark 環境設定 .NET 的詳細資訊，請參閱 [快速入門教學](../tutorials/get-started.md) 課程。</span><span class="sxs-lookup"><span data-stu-id="349e3-113">See the [getting started tutorial](../tutorials/get-started.md) for more information on setting up your .NET for Apache Spark environment.</span></span>

## <a name="prepare-environment"></a><span data-ttu-id="349e3-114">準備環境</span><span class="sxs-lookup"><span data-stu-id="349e3-114">Prepare environment</span></span>

<span data-ttu-id="349e3-115">若要使用 Jupyter 筆記本，您需要兩個專案。</span><span class="sxs-lookup"><span data-stu-id="349e3-115">To work with Jupyter Notebooks, you'll need two things.</span></span>

1. <span data-ttu-id="349e3-116">安裝 [.Net Interactive global .net 工具](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span><span class="sxs-lookup"><span data-stu-id="349e3-116">Install the [.NET Interactive global .NET tool](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span></span>
1. <span data-ttu-id="349e3-117">下載 `Microsoft.Spark` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="349e3-117">Download the `Microsoft.Spark` NuGet package.</span></span>
    1. <span data-ttu-id="349e3-118">流覽至 [ [Microsoft Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件] 頁面。</span><span class="sxs-lookup"><span data-stu-id="349e3-118">Navigate to the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package page.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="349e3-119">根據預設，會下載最新版本的套件。</span><span class="sxs-lookup"><span data-stu-id="349e3-119">By default, the latest version of the package is downloaded.</span></span> <span data-ttu-id="349e3-120">**請確定您下載的版本與 Apache Spark .NET Worker 相同。**</span><span class="sxs-lookup"><span data-stu-id="349e3-120">**Make sure that the version you download is the same as your Apache Spark .NET Worker.**</span></span>

    1. <span data-ttu-id="349e3-121">在 [ **資訊** ] 窗格中，選取 [ **下載套件** ] 以下載最新版本的套件。</span><span class="sxs-lookup"><span data-stu-id="349e3-121">In the **Info** pane, select **Download package** to download the latest version of the package.</span></span> <span data-ttu-id="349e3-122">封裝的名稱類似于  *microsoft。封裝版本]. nupkg*。</span><span class="sxs-lookup"><span data-stu-id="349e3-122">The name of the package is similar to  *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span></span>
    1. <span data-ttu-id="349e3-123">將下載的封裝解壓縮。</span><span class="sxs-lookup"><span data-stu-id="349e3-123">Unzip the downloaded package.</span></span> <span data-ttu-id="349e3-124">解壓縮的目錄應包含稱為 *jar*的子目錄。</span><span class="sxs-lookup"><span data-stu-id="349e3-124">The unzipped directory should contain a subdirectory called *jars*.</span></span> <span data-ttu-id="349e3-125">記下路徑，因為稍後會用到。</span><span class="sxs-lookup"><span data-stu-id="349e3-125">Take note of the path since it's used at a later time.</span></span>

## <a name="start-net-for-apache-spark"></a><span data-ttu-id="349e3-126">啟動 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="349e3-126">Start .NET for Apache Spark</span></span>

<span data-ttu-id="349e3-127">執行下列命令，以在「偵錯工具」模式中啟動 Apache Spark 的 .NET。</span><span class="sxs-lookup"><span data-stu-id="349e3-127">Run the following command to start .NET for Apache Spark in debug mode.</span></span> <span data-ttu-id="349e3-128">此 `spark-submit` 命令會啟動進程，並等候來自 [SparkSession](xref:Microsoft.Spark.Sql.SparkSession)的連接。</span><span class="sxs-lookup"><span data-stu-id="349e3-128">This `spark-submit` command starts a process and waits for connections from a [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span> <span data-ttu-id="349e3-129">請務必針對您所使用的 Apache Spark，提供 `microsoft-spark-<version>.jar` 適用于 .net 的個別版本的路徑。</span><span class="sxs-lookup"><span data-stu-id="349e3-129">Make sure to provide the path to the `microsoft-spark-<version>.jar` for the respective version of .NET for Apache Spark you're using.</span></span>

<span data-ttu-id="349e3-130">**Ubuntu**</span><span class="sxs-lookup"><span data-stu-id="349e3-130">**Ubuntu**</span></span>

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

<span data-ttu-id="349e3-131">**Windows**</span><span class="sxs-lookup"><span data-stu-id="349e3-131">**Windows**</span></span>

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a><span data-ttu-id="349e3-132">建立 Notebook</span><span class="sxs-lookup"><span data-stu-id="349e3-132">Create a notebook</span></span>

<span data-ttu-id="349e3-133">您可以使用不同的介面來與 Jupyter 互動。</span><span class="sxs-lookup"><span data-stu-id="349e3-133">You can use different interfaces to interact with Jupyter.</span></span> <span data-ttu-id="349e3-134">針對以瀏覽器為基礎的介面，請使用 Jupyter 筆記本或 Jupyter Lab。</span><span class="sxs-lookup"><span data-stu-id="349e3-134">For a browser-based interface, use Jupyter Notebooks or Jupyter Lab.</span></span> <span data-ttu-id="349e3-135">如需本機編輯器體驗，請使用 VS Code。</span><span class="sxs-lookup"><span data-stu-id="349e3-135">For a local editor experience, use VS Code.</span></span>

### <a name="jupyter-notebooks--jupyter-lab"></a><span data-ttu-id="349e3-136">Jupyter 筆記本 & Jupyter Lab</span><span class="sxs-lookup"><span data-stu-id="349e3-136">Jupyter Notebooks & Jupyter Lab</span></span>

1. <span data-ttu-id="349e3-137">在另一個命令提示字元中，使用下列其中一個命令開始 Jupyter Notebook 或 Jupyter Lab：</span><span class="sxs-lookup"><span data-stu-id="349e3-137">In another command prompt, start Jupyter Notebook or Jupyter Lab using one of the commands below:</span></span>

    <span data-ttu-id="349e3-138">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="349e3-138">**Jupyter Notebook**</span></span>

    ```bash
    jupyter notebook
    ```

    <span data-ttu-id="349e3-139">**Jupyter 實驗室**</span><span class="sxs-lookup"><span data-stu-id="349e3-139">**Jupyter Lab**</span></span>

    ```bash
    jupyter lab
    ```

    <span data-ttu-id="349e3-140">這些命令會使用 Jupyter Notebook 或 Jupyter Lab 介面啟動瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="349e3-140">These commands launch a browser window with the Jupyter Notebook or Jupyter Lab interface.</span></span>

1. <span data-ttu-id="349e3-141">在瀏覽器中，建立新的筆記本。</span><span class="sxs-lookup"><span data-stu-id="349e3-141">In the browser, create a new notebook.</span></span>

    <span data-ttu-id="349e3-142">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="349e3-142">**Jupyter Notebook**</span></span>

    <span data-ttu-id="349e3-143">選取 \*\*新的 > .net (c # ) \*\* 或 \*\*新的 > .net (F # ) \*\*</span><span class="sxs-lookup"><span data-stu-id="349e3-143">Select **New > .NET (C#)** or **New > .NET (F#)**</span></span>

    <span data-ttu-id="349e3-144">**Jupyter 實驗室**</span><span class="sxs-lookup"><span data-stu-id="349e3-144">**Jupyter Lab**</span></span>

    <span data-ttu-id="349e3-145">在啟動器視窗中，選取 \*\*.net (c # ) \*\* 或 \*\*.net (F # ) \*\*</span><span class="sxs-lookup"><span data-stu-id="349e3-145">In the Launcher window, select **.NET (C#)** or **.NET (F#)**</span></span>

### <a name="visual-studio-code-preview"></a><span data-ttu-id="349e3-146">Visual Studio Code (preview) </span><span class="sxs-lookup"><span data-stu-id="349e3-146">Visual Studio Code (preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="349e3-147">若要在 VS Code 中使用 Jupyter 筆記本，您必須安裝：</span><span class="sxs-lookup"><span data-stu-id="349e3-147">To use Jupyter Notebooks in VS Code, you have to install:</span></span>
>
>- [<span data-ttu-id="349e3-148">VS Code 內部人員</span><span class="sxs-lookup"><span data-stu-id="349e3-148">VS Code Insiders</span></span>](https://code.visualstudio.com/insiders/)
>- [<span data-ttu-id="349e3-149">.NET 互動式筆記本擴充功能</span><span class="sxs-lookup"><span data-stu-id="349e3-149">.NET Interactive Notebooks extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. <span data-ttu-id="349e3-150">開啟 VS Code。</span><span class="sxs-lookup"><span data-stu-id="349e3-150">Open VS Code.</span></span>
1. <span data-ttu-id="349e3-151">開啟 [命令選擇區] **> 命令**選擇區。</span><span class="sxs-lookup"><span data-stu-id="349e3-151">Open the command palette **View > Command Palette**.</span></span>

    <span data-ttu-id="349e3-152">當命令選擇區出現時，輸入下列命令以建立新的 .NET 互動式筆記本：</span><span class="sxs-lookup"><span data-stu-id="349e3-152">When the command palette appears, enter the following command to create a new .NET Interactive notebook:</span></span>

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    <span data-ttu-id="349e3-153">或者，如果您想要以 *.ipynb* 副檔名開啟現有的 .net 互動式筆記本，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="349e3-153">Alternatively, if you want to open an existing .NET Interactive notebook with the *.ipynb* extension, use the following command:</span></span>

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a><span data-ttu-id="349e3-154">初始化 Spark 會話</span><span class="sxs-lookup"><span data-stu-id="349e3-154">Initialize a Spark Session</span></span>

1. <span data-ttu-id="349e3-155">筆記本開啟時，請安裝 `Microsoft.Spark` NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="349e3-155">When the notebook opens, install the `Microsoft.Spark` NuGet package.</span></span> <span data-ttu-id="349e3-156">請確定您安裝的版本與 .NET 背景工作相同。</span><span class="sxs-lookup"><span data-stu-id="349e3-156">Make sure the version you install is the same as the .NET Worker.</span></span>

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. <span data-ttu-id="349e3-157">將下列 using 語句新增至筆記本。</span><span class="sxs-lookup"><span data-stu-id="349e3-157">Add the following using statement to the notebook.</span></span>

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. <span data-ttu-id="349e3-158">初始化您的 [SparkSession](xref:Microsoft.Spark.Sql.SparkSession)。</span><span class="sxs-lookup"><span data-stu-id="349e3-158">Initialize your [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span>

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

<span data-ttu-id="349e3-159">筆記本看起來應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="349e3-159">The notebook should look similar to the one in the following image.</span></span> <span data-ttu-id="349e3-160">此範例使用 VS Code，但 Jupyter Notebook 和 Jupyter 實驗室應該看起來相同。</span><span class="sxs-lookup"><span data-stu-id="349e3-160">This example uses VS Code, but Jupyter Notebook and Jupyter Lab should look about the same.</span></span>

> [!div class="mx-imgBorder"]
<span data-ttu-id="349e3-161">![適用于 Apache Spark Jupyter Notebook VS Code 的 .NET](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span><span class="sxs-lookup"><span data-stu-id="349e3-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span></span>

## <a name="next-steps"></a><span data-ttu-id="349e3-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="349e3-162">Next Steps</span></span>

- [<span data-ttu-id="349e3-163">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="349e3-163">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
- [<span data-ttu-id="349e3-164">使用 .NET 針對 Apache Spark 和 ML.NET 預測情感</span><span class="sxs-lookup"><span data-stu-id="349e3-164">Predict sentiment using .NET for Apache Spark and ML.NET</span></span>](../tutorials/ml-sentiment-analysis.md)
- <span data-ttu-id="349e3-165">如需 .NET Interactive 的詳細資訊，請參閱 [.Net 互動式檔](https://github.com/dotnet/interactive/blob/main/docs/README.md)集。</span><span class="sxs-lookup"><span data-stu-id="349e3-165">For more information on .NET Interactive, see the [.NET Interactive documentation](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span></span>
