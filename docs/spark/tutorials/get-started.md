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
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>教程： 開始與 .NET 的阿帕奇火花

本教程教您如何在 Windows、MacOS 和 Ubuntu 上使用 .NET 核心運行 Apache Spark 應用的 .NET。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 為 .NET 為 Apache Spark 準備您的環境
> * 為 Apache Spark 應用程式編寫您的第一個 .NET
> * 為 Apache Spark 應用程式構建並運行您的簡單 .NET

## <a name="prepare-your-environment"></a>準備您的環境

在開始編寫應用之前，需要設置一些先決條件依賴項。 如果可以從命令列`dotnet`環境中`java`運行`mvn` `spark-shell` 、、則環境已準備就緒，可以跳到下一節。 如果無法運行任何或所有命令，則執行以下步驟。

### <a name="1-install-net"></a>1. 安裝 .NET

要開始構建 .NET 應用，您需要下載並安裝 .NET SDK（軟體發展工具組）。

下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。 安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。

安裝 .NET 核心 SDK 後，打開新的命令提示符或終端並運行`dotnet`。

如果命令運行並列印出有關如何使用 dotnet 的資訊，則可以移動到下一步。 如果收到`'dotnet' is not recognized as an internal or external command`錯誤，請確保在運行該命令之前打開了**新的**命令提示符或終端。

### <a name="2-install-java"></a>2. 安裝 JAVA

為 Windows 和 MacOS 安裝[JAVA 8.1，](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)為 Ubuntu[安裝 OpenJDK 8。](https://openjdk.java.net/install/)

為您的作業系統選取適當版本。 例如，為 Windows x64 電腦選擇**jdk-8u201-windows-x64.exe（** 如下所示）或適用于 MacOS 的**jdk-8u231-macosx-x64.dmg。** 然後，使用 命令`java`驗證安裝。

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. 安裝壓縮軟體

Apache Spark 下載為壓縮 .tgz 檔。 使用提取程式（如[7-Zip](https://www.7-zip.org/)或[WinZip）](https://www.winzip.com/)提取檔。

### <a name="4-install-apache-spark"></a>4. 安裝阿帕奇火花

[下載並安裝阿帕奇火花](https://spark.apache.org/downloads.html)。 您需要從版本 2.3.* 或 2.4.0、2.4.1、2.4.3 或 2.4.4（阿帕奇 Spark 的 NET 與其他版本的 Apache Spark 相容）中選擇。

以下步驟中使用的命令假定您[已下載並安裝了 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。 如果要使用其他版本，請將**2.4.1**替換為相應的版本號。 然後，提取 **.tar**檔和 Apache Spark 檔。

要提取嵌套的 **.tar**檔，

* 找到您下載的**spark-2.4.1-bin-hadoop2.7.tgz**檔。
* 按右鍵該檔，並在此處選擇**7-Zip-> 提取**。
* **spark-2.4.1-bin-hadoop2.7.tar**與您下載的 **.tgz**檔一起創建。

要提取阿帕奇火花檔：

* 按右鍵**spark-2.4.1-bin-hadoop2.7.tar**並選擇**7-Zip-> 提取檔...**
* 在 **"提取到"** 欄位中輸入**C：\bin。**
* 取消選中 **"提取到**欄位"下的核取方塊。
* 選取 [確定]****。
* Apache Spark 檔被提取到 C：\bin_spark-2.4.1-bin-hadoop2.7]

![安裝 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

運行以下命令以設置用於在**Windows**上查找 Apache Spark 的環境變數：

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

運行以下命令以設置用於在**MacOS**和**Ubuntu**上定位 Apache Spark 的環境變數：

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

安裝所有內容並設置環境變數後，打開**新的**命令提示符或終端並運行以下命令：

`%SPARK_HOME%\bin\spark-submit --version`

如果命令運行並列印版本資訊，則可以移動到下一步。

如果收到`'spark-submit' is not recognized as an internal or external command`錯誤，請確保打開**新的**命令提示符。

### <a name="5-install-net-for-apache-spark"></a>5. 安裝 .NET 用於阿帕奇火花

從阿帕奇 Spark GitHub 的 .NET 下載[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases)版本。 例如，如果您在 Windows 電腦上並計畫使用 .NET Core，[請下載 Windows x64 netcoreapp3.1 版本](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)。

要提取 Microsoft.Spark.Worker：

* 找到您下載的**Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip**檔。
* 按右鍵並選擇**7-Zip -> 提取檔...**
* 在 **"提取到"** 欄位中輸入**C：\bin。**
* 取消選中 **"提取到**欄位"下的核取方塊。
* 選取 [確定]****。

![安裝 .NET 火花](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. 安裝 WinUtils（僅限 Windows）

阿帕奇火花的 .NET 要求與阿帕奇火花一起安裝 WinUtils。 [下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). 然後，將 WinUtils 複製到**C：\bin_spark-2.4.1-bin hadoop2.7\bin**。

> [!NOTE]
> 如果您使用的是其他版本的 Hadoop（在 Spark 安裝資料夾名稱的末尾帶有批號，請選擇與您的 Hadoop 版本相容的[WinUtils 版本](https://github.com/steveloughran/winutils)。

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. 設置DOTNET_WORKER_DIR並檢查依賴項

運行以下命令之一以設置`DOTNET_WORKER_DIR`環境變數，.NET 應用使用該變數查找阿帕奇 Spark 的 .NET。

在**Windows**上，創建新[的環境變數](https://www.java.com/en/download/help/path.xml)`DOTNET_WORKER_DIR`，並將其設置為下載並提取 Microsoft.Spark.Worker（例如）。 `C:\bin\Microsoft.Spark.Worker\`

在**MacOS**上，使用`export DOTNET_WORKER_DIR <your_path>`創建新的環境變數並將其設置為下載並提取 Microsoft.Spark.Worker 的目錄（例如 *，*/bin/Microsoft.Spark.Worker/）。*

在**Ubuntu**上，創建新[的環境變數](https://help.ubuntu.com/community/EnvironmentVariables)`DOTNET_WORKER_DIR`，並將其設置為下載並提取 Microsoft.Spark.Worker 的目錄（例如 *，\/bin/Microsoft.Spark.Worker）。*

最後，在移動到下一節之前，`dotnet`仔細檢查`java`是否可以`mvn`從`spark-shell`命令列運行 。。"

## <a name="write-a-net-for-apache-spark-app"></a>撰寫適用於 Apache Spark 的 .NET 應用程式

### <a name="1-create-a-console-app"></a>1. 創建主控台應用

在命令提示符或終端中，運行以下命令以創建新的主控台應用程式：

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

該`dotnet`命令為您創建`new`類型`console`應用程式。 該`-o`參數創建一個名為*mySparkApp*的目錄，其中存儲你的應用，並將其填充到所需的檔中。 該`cd mySparkApp`命令將目錄更改為您剛剛創建的應用目錄。

### <a name="2-install-nuget-package"></a>2. 安裝 NuGet 包

要在應用中使用的阿帕奇 Spark 的 .NET，請安裝 Microsoft.Spark 包。 在命令提示符或終端中，運行以下命令：

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. 對應用進行編碼

打開 Visual Studio 代碼或任何文字編輯器中的*Program.cs，* 並將所有代碼替換為以下內容：

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

### <a name="4-create-and-add-a-data-file"></a>4. 創建並添加資料檔案

打開命令提示符或終端並導航到應用資料夾。

```bash
cd <your-app-output-directory>
```

你的應用處理包含文本行的檔。 在*mySparkApp*目錄中創建*輸入.txt*檔，其中包含以下文本：

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>執行適用於 Apache Spark 的 .NET 應用程式

1. 運行以下命令來生成應用程式：

   ```dotnetcli
   dotnet build
   ```

2. 運行以下命令以提交應用程式以在 Apache Spark 上運行：

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > 此命令假定您已下載 Apache Spark 並將其添加到您的 PATH 環境變數，以便能夠使用`spark-submit`。 否則，您必須使用完整路徑（例如 *，C：\bin_apache-spark_bin_spark-提交*或 *_/spark/bin/spark 提交*）。

3. 應用運行時 *，input.txt*檔的字計數資料將寫入主控台。

恭喜！ 您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 為適用於 Apache Spark 的 .NET 準備您的 Windows 環境
> * 為 Apache Spark 應用程式編寫您的第一個 .NET
> * 為 Apache Spark 應用程式構建並運行您的簡單 .NET

要查看解釋上述步驟的視頻，請查看 Apache Spark [101 視頻系列的 .NET。](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)

若要深入了解，請查看資源頁面。
> [!div class="nextstepaction"]
> [適用於 Apache Spark 的 .NET 資源](../resources/index.md)
