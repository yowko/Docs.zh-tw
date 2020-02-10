---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows、MacOS 和 Ubuntu 上使用 .NET Core 來執行適用于 Apache Spark 應用程式的 .NET。
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 018c21804bf942233e07039281d7ec22a6bef763
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092313"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>教學課程：開始使用適用于 Apache Spark 的 .NET

本教學課程會教您如何在 Windows、MacOS 和 Ubuntu 上使用 .NET Core 來執行適用于 Apache Spark 應用程式的 .NET。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 準備適用于 .NET 的環境以進行 Apache Spark
> * 撰寫 Apache Spark 應用程式的第一個 .NET
> * 為 Apache Spark 應用程式建立及執行您的簡單 .NET

## <a name="prepare-your-environment"></a>準備您的環境

開始撰寫應用程式之前，您必須先設定一些必要的相依性。 如果您可以從命令列環境執行 `dotnet`、`java`、`mvn``spark-shell`，則您的環境已準備就緒，您可以跳到下一節。 如果您無法執行任何或所有的命令，請執行下列步驟。

### <a name="1-install-net"></a>1. 安裝 .NET

若要開始建立 .NET 應用程式，您必須下載並安裝 .NET SDK （軟體發展工具組）。

下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。 安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。

安裝 .NET Core SDK 之後，請開啟新的命令提示字元或終端機，然後執行 `dotnet`。

如果命令執行並印出有關如何使用 dotnet 的資訊，可以移至下一個步驟。 如果您收到 `'dotnet' is not recognized as an internal or external command` 錯誤，請確定您在執行命令之前，已開啟**新**的命令提示字元或終端機。

### <a name="2-install-java"></a>2. 安裝 JAVA

安裝適用于 Windows 和 MacOS 的[JAVA 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) ，或適用于 Ubuntu 的[OpenJDK 8](https://openjdk.java.net/install/) 。

為您的作業系統選取適當版本。 例如，選取 Windows x64 電腦的**jdk-8u201-windows-x64** （如下所示）或**jdk-8u231-macosx-x64. dmg** for MacOS。 然後，使用命令 `java` 來確認安裝。

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. 安裝壓縮軟體

Apache Spark 會下載為 tgz 檔案。 使用類似[7-Zip](https://www.7-zip.org/)或[WinZip](https://www.winzip.com/)的抽取程式來解壓縮檔案。

### <a name="4-install-apache-spark"></a>4. 安裝 Apache Spark

[下載並安裝 Apache Spark](https://spark.apache.org/downloads.html)。 您必須選取版本 2.3. * 或2.4.0、2.4.1、2.4.3 或2.4.4 （適用于 Apache Spark 的 .NET 與 Apache Spark 的其他版本不相容）。

下列步驟中使用的命令假設您已[下載並安裝 Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)。 如果您想要使用不同的版本，請將**2.4.1**取代為適當的版本號碼。 然後，將**tar**檔案和 Apache Spark 檔案解壓縮。

若要解壓縮嵌套的**tar**檔案：

* 找出您已下載的**spark-2.4.1-bin-hadoop 2.7. tgz**檔案。
* 以滑鼠右鍵按一下檔案，然後選取 [ **7-Zip-> 解壓縮到這裡**]。
* **spark-2.4.1-bin-hadoop 2.7. tar**會連同您下載的**tgz**檔案一起建立。

若要解壓縮 Apache Spark 檔案：

* 以滑鼠右鍵按一下 [ **spark-2.4.1-bin-hadoop 2.7. tar** ]，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]
* 在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。
* 取消核**取 [解壓縮至**] 欄位下方的核取方塊。
* 選取 [確定]。
* Apache Spark 檔案會解壓縮至 C:\bin\spark-2.4.1-bin-hadoop2.7\

![安裝 Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

執行下列命令，設定用來在**Windows**上尋找 Apache Spark 的環境變數：

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

執行下列命令，設定用來在**MacOS**和**Ubuntu**上尋找 Apache Spark 的環境變數：

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

安裝所有專案並設定您的環境變數之後，請開啟**新**的命令提示字元或終端機，然後執行下列命令：

`%SPARK_HOME%\bin\spark-submit --version`

如果命令執行並列印版本資訊，您可以移至下一個步驟。

如果您收到 `'spark-submit' is not recognized as an internal or external command` 錯誤，請確定您已開啟**新**的命令提示字元。

### <a name="5-install-net-for-apache-spark"></a>5. 安裝適用于 Apache Spark 的 .NET

從適用于 Apache Spark GitHub 的 .NET 下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases)版本。 例如，如果您是在 Windows 電腦上，並打算使用 .NET Core，請[下載 windows x64 netcoreapp 3.1 版](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)。

若要解壓縮 Microsoft. Spark. Worker：

* 找出您下載的**netcoreapp 3.1. win-x64-0.8.0 版 .zip**檔案。
* 按一下滑鼠右鍵，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]。
* 在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。
* 取消核**取 [解壓縮至**] 欄位下方的核取方塊。
* 選取 [確定]。

![安裝 .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. 安裝 Winutils.exe （僅限 Windows）

適用于 Apache Spark 的 .NET 需要與 Apache Spark 一起安裝 Winutils.exe。 [下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。 然後，將 Winutils.exe 複製到**C:\bin\spark-2.4.1-bin-hadoop2.7\bin**。

> [!NOTE]
> 如果您使用的是不同版本的 Hadoop （在 Spark 安裝資料夾名稱的結尾加上批註），請選取與您的 Hadoop 版本相容的[winutils.exe 版本](https://github.com/steveloughran/winutils)。

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. 設定 DOTNET_WORKER_DIR 並檢查相依性

執行下列其中一個命令來設定 `DOTNET_WORKER_DIR` 環境變數，以供 .NET 應用程式用來尋找 Apache Spark 的 .NET。

在**Windows**上，`DOTNET_WORKER_DIR` 建立[新的環境變數](https://www.java.com/en/download/help/path.xml)，並將它設定為您下載並解壓縮的目錄（例如，`C:\bin\Microsoft.Spark.Worker\`）。

在**MacOS**上，使用 `export DOTNET_WORKER_DIR <your_path>` 建立新的環境變數，並將它設定為您下載並解壓縮的目錄（例如 *~/bin/Microsoft.Spark.Worker/* ）。 

在**Ubuntu**上，`DOTNET_WORKER_DIR` 建立[新的環境變數](https://help.ubuntu.com/community/EnvironmentVariables)，並將它設定為您下載並解壓縮的目錄（例如 *~/bin/Microsoft.Spark.Worker*）。

最後，再次檢查您可以從命令列執行 `dotnet`、`java`、`mvn``spark-shell`，然後再移到下一節。

## <a name="write-a-net-for-apache-spark-app"></a>撰寫適用於 Apache Spark 的 .NET 應用程式

### <a name="1-create-a-console-app"></a>1. 建立主控台應用程式

在您的命令提示字元或終端機中，執行下列命令來建立新的主控台應用程式：

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

`dotnet` 命令會為您建立類型為 `console` 的 `new` 應用程式。 `-o` 參數會建立名為*mySparkApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。 `cd mySparkApp` 命令會將目錄變更為您剛才建立的應用程式目錄。

### <a name="2-install-nuget-package"></a>2. 安裝 NuGet 套件

若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在您的命令提示字元或終端機中，執行下列命令：

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. 編碼您的應用程式

在 Visual Studio Code 或任何文字編輯器中開啟*Program.cs* ，並將所有程式碼取代為下列內容：

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

### <a name="4-create-and-add-a-data-file"></a>4. 建立和新增資料檔案

開啟命令提示字元或終端機，並流覽至您的應用程式資料夾。

```bash
cd <your-app-output-directory>
```

您的應用程式會處理包含文字行的檔案。 在您的*mySparkApp*目錄中建立*輸入 .txt*檔案，其中包含下列文字：

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>執行適用於 Apache Spark 的 .NET 應用程式

1. 執行下列命令來建立您的應用程式：

   ```dotnetcli
   dotnet build
   ```

2. 執行下列命令，以提交要在 Apache Spark 上執行的應用程式：

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > 此命令假設您已下載 Apache Spark 並將它新增至您的 PATH 環境變數，以便能夠使用 `spark-submit`。 否則，您必須使用完整路徑（例如， *C:\bin\apache-spark\bin\spark-submit*或 *~/spark/bin/spark-submit*）。

3. 當您的應用程式執行時，會將*輸入 .txt*檔案的字數統計資料寫入主控台。

恭喜！ 您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 為適用於 Apache Spark 的 .NET 準備您的 Windows 環境
> * 撰寫 Apache Spark 應用程式的第一個 .NET
> * 為 Apache Spark 應用程式建立及執行您的簡單 .NET

若要觀看說明上述步驟的影片，請參閱[適用于 Apache Spark 101 的 .net 影片系列](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。

若要深入了解，請查看資源頁面。
> [!div class="nextstepaction"]
> [適用於 Apache Spark 的 .NET 資源](../resources/index.md)
