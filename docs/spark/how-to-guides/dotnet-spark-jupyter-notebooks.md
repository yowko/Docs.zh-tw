---
title: 使用 Jupyter Notebook
titleSuffix: .NET for Apache Spark
description: '在互動式環境中使用 .NET 進行 Apache Spark，例如 Jupyter Notebook、Jupyter Lab 或 Visual Studio Code (VS Code) '
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: cf19b4e4b7a7b9033fb97b2b2736ab0383c11f93
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96598929"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a>在 Jupyter 筆記本中使用 .NET 進行 Apache Spark

在本文中，您將瞭解如何以互動方式，在 Jupyter Notebook 中以互動方式執行 Apache Spark 工作，並使用 .NET Interactive Visual Studio Code (VS Code) 。

## <a name="about-jupyter"></a>關於 Jupyter

[Jupyter](https://jupyter.org/) 是開放原始碼的跨平臺運算環境，可讓使用者以互動方式原型設計和開發應用程式。 您可以透過各種不同的介面（例如 Jupyter Notebook、Jupyter Lab 和 VS Code）來與 Jupyter 互動。

在 .NET 的環境中，.net [Interactive](https://github.com/dotnet/interactive)（.net Core 通用工具）提供核心，可在互動式運算環境（例如 Jupyter Notebook）中撰寫 .net 程式碼 (c #/f # ) 。

## <a name="prerequisites"></a>必要條件

- [.NET Core 3.1 SDK](../../core/install/index.yml)
- [Apache Spark](https://spark.apache.org/downloads.html)
- [Apache Spark .NET 背景工作](https://github.com/dotnet/spark/releases)

如需有關為 Apache Spark 環境設定 .NET 的詳細資訊，請參閱 [快速入門教學](../tutorials/get-started.md) 課程。

## <a name="prepare-environment"></a>準備環境

若要使用 Jupyter 筆記本，您需要兩個專案。

1. 安裝 [.Net Interactive global .net 工具](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
1. 下載 `Microsoft.Spark` NuGet 套件。
    1. 流覽至 [ [Microsoft Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件] 頁面。

        > [!IMPORTANT]
        > 根據預設，會下載最新版本的套件。 **請確定您下載的版本與 Apache Spark .NET Worker 相同。**

    1. 在 [ **資訊** ] 窗格中，選取 [ **下載套件** ] 以下載最新版本的套件。 封裝的名稱類似于  *microsoft。封裝版本]. nupkg*。
    1. 將下載的封裝解壓縮。 解壓縮的目錄應包含稱為 *jar* 的子目錄。 記下路徑，因為稍後會用到。

## <a name="start-net-for-apache-spark"></a>啟動 Apache Spark 的 .NET

執行下列命令，以在「偵錯工具」模式中啟動 Apache Spark 的 .NET。 此 `spark-submit` 命令會啟動進程，並等候來自 [SparkSession](xref:Microsoft.Spark.Sql.SparkSession)的連接。 請務必針對您所使用的 Apache Spark，提供 `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` 適用于 .net 的個別版本的路徑。

**Ubuntu**

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

**Windows**

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a>建立 Notebook

您可以使用不同的介面來與 Jupyter 互動。 針對以瀏覽器為基礎的介面，請使用 Jupyter 筆記本或 Jupyter Lab。 如需本機編輯器體驗，請使用 VS Code。

### <a name="jupyter-notebooks--jupyter-lab"></a>Jupyter 筆記本 & Jupyter Lab

1. 在另一個命令提示字元中，使用下列其中一個命令開始 Jupyter Notebook 或 Jupyter Lab：

    **Jupyter Notebook**

    ```bash
    jupyter notebook
    ```

    **Jupyter 實驗室**

    ```bash
    jupyter lab
    ```

    這些命令會使用 Jupyter Notebook 或 Jupyter Lab 介面啟動瀏覽器視窗。

1. 在瀏覽器中，建立新的筆記本。

    **Jupyter Notebook**

    選取 **新的 > .net (c # )** 或 **新的 > .net (F # )**

    **Jupyter 實驗室**

    在啟動器視窗中，選取 **.net (c # )** 或 **.net (F # )**

### <a name="visual-studio-code-preview"></a>Visual Studio Code (preview) 

> [!IMPORTANT]
> 若要在 VS Code 中使用 Jupyter 筆記本，您必須安裝：
>
>- [VS Code 內部人員](https://code.visualstudio.com/insiders/)
>- [.NET 互動式筆記本擴充功能](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. 開啟 VS Code。
1. 開啟 [命令選擇區] **> 命令** 選擇區。

    當命令選擇區出現時，輸入下列命令以建立新的 .NET 互動式筆記本：

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    或者，如果您想要以 *.ipynb* 副檔名開啟現有的 .net 互動式筆記本，請使用下列命令：

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a>初始化 Spark 會話

1. 筆記本開啟時，請安裝 `Microsoft.Spark` NuGet 套件。 請確定您安裝的版本與 .NET 背景工作相同。

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. 將下列 using 語句新增至筆記本。

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. 初始化您的 [SparkSession](xref:Microsoft.Spark.Sql.SparkSession)。

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

筆記本看起來應該如下圖所示。 此範例使用 VS Code，但 Jupyter Notebook 和 Jupyter 實驗室應該看起來相同。

> [!div class="mx-imgBorder"]
![適用于 Apache Spark Jupyter Notebook VS Code 的 .NET](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)

## <a name="next-steps"></a>後續步驟

- [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
- [使用 .NET 針對 Apache Spark 和 ML.NET 預測情感](../tutorials/ml-sentiment-analysis.md)
- 如需 .NET Interactive 的詳細資訊，請參閱 [.Net 互動式檔](https://github.com/dotnet/interactive/blob/main/docs/README.md)集。
