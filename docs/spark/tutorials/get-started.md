---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows、macOS 和 Ubuntu 上使用 .NET Core 執行適用于 Apache Spark 應用程式的 .NET。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 16ccc8f40f290c4bc10f03d1f4d1b296b17f6b11
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687816"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>教學課程：開始使用 .NET 進行 Apache Spark

本教學課程會教您如何在 Windows、macOS 和 Ubuntu 上使用 .NET Core 執行 Apache Spark 應用程式的 .NET。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 準備適用于 .NET 的環境以進行 Apache Spark
> * 為 Apache Spark 應用程式撰寫您的第一個 .NET
> * 為 Apache Spark 應用程式建立並執行您的 .NET

## <a name="prepare-your-environment"></a>準備您的環境

在開始撰寫您的應用程式之前，您必須先設定一些必要條件的相依性。 如果您可以 `dotnet` `java` `spark-shell` 從命令列環境執行，則您的環境已備妥，您可以跳到下一節。 如果您無法執行任何或所有命令，請執行下列步驟。

### <a name="1-install-net"></a>1. 安裝 .NET

若要開始建立 .NET 應用程式，您必須下載並安裝 .NET SDK (軟體發展工具組) 。

下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)。 安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。

安裝 .NET Core SDK 之後，請開啟新的命令提示字元或終端機，然後執行 `dotnet` 。

如果命令執行並印出如何使用 dotnet 的相關資訊，則可以移至下一個步驟。 如果您收到 `'dotnet' is not recognized as an internal or external command` 錯誤，請務必先開啟 **新** 的命令提示字元或終端機，然後再執行命令。

### <a name="2-install-java"></a>2. 安裝 JAVA

安裝適用于 Windows 和 macOS 的 [JAVA 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) ，或適用于 Ubuntu 的 [OpenJDK 8](https://openjdk.java.net/install/) 。

為您的作業系統選取適當版本。 例如，選取 Windows x64 電腦的 **jdk-8u201-windows-x64.exe** (如下所示) 或 **jdk-8u231-macosx-x64. dmg** for macOS。 然後，使用命令 `java` 來確認安裝。

![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. 安裝壓縮軟體

Apache Spark 會下載為壓縮的 tgz 檔案。 使用類似 [7-Zip](https://www.7-zip.org/) 或 [WinZip](https://www.winzip.com/)的解壓縮程式來解壓縮檔案。

### <a name="4-install-apache-spark"></a>4. 安裝 Apache Spark

[下載並安裝 Apache Spark](https://spark.apache.org/downloads.html)。 您必須從 2.3. * 或2.4.0、2.4.1、2.4.3、2.4.4、2.4.5、2.4.6、2.4.7 版、3.0.0 或3.0.1 版 ( .NET for Apache Spark 與其他 Apache Spark) 版本不相容。

下列步驟中使用的命令假設您已 [下載並安裝 Apache Spark 3.0.1](https://spark.apache.org/downloads.html)。 如果您想要使用不同的版本，請將 **3.0.1** 取代為適當的版本號碼。 然後，將 **tar** 檔案和 Apache Spark 檔案解壓縮。

若要將嵌套的 **tar** 檔案解壓縮：

* 找出您下載的 **spark-3.0.1-bin-hadoop 2.7. tgz** 檔案。
* 以滑鼠右鍵按一下檔案，然後選取 [ **7-Zip-> 解壓縮到這裡**]。
* **spark-3.0.1-bin-hadoop 2.7. tar** 會與您下載的 **tgz** 檔案一起建立。

解壓縮 Apache Spark 檔案：

* 以滑鼠右鍵按一下 **spark-3.0.1-bin-hadoop 2.7. tar** ，然後選取 [ **7-Zip-> 解壓縮檔案 ...** ]
* 在 [**解壓縮至**] 欄位中輸入 **C:\bin** 。
* 取消核 **取 [解壓縮至** ] 欄位下方的核取方塊。
* 選取 [確定]。
* Apache Spark 檔案會解壓縮至 C:\bin\spark-3.0.1-bin-hadoop2.7\

![安裝 Spark](./media/spark-extract-with-7-zip.png)

執行下列命令以設定用來尋找 Apache Spark 的環境變數。 在 Windows 上，請務必在系統管理員模式中執行命令提示字元。

#### <a name="windows"></a>[Windows](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-3.0.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-3.0.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin"
```

#### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-3.0.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

當您安裝所有專案並設定環境變數之後，請開啟 **新** 的命令提示字元或終端機，然後執行下列命令：

```text
spark-submit --version
```

如果命令執行並列印版本資訊，您可以移至下一個步驟。

如果您收到 `'spark-submit' is not recognized as an internal or external command` 錯誤，請確定您已開啟 **新** 的命令提示字元。

### <a name="5-install-net-for-apache-spark"></a>5. 安裝適用于 Apache Spark 的 .NET

從 .NET 下載 Apache Spark GitHub 的[。](https://github.com/dotnet/spark/releases) 例如，如果您是在 Windows 電腦上，並打算使用 .NET Core，請 [下載 windows x64 netcoreapp 3.1 版本](https://github.com/dotnet/spark/releases)。

若要將 Microsoft. 背景工作角色解壓縮：

* 找出您下載的 **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-1.0.0.zip** 檔案。
* 以滑鼠右鍵按一下並選取 [ **7-Zip-> 解壓縮檔** 案 ...]。
* 在 [**解壓縮至**] 欄位中輸入 **C:\bin** 。
* 取消核 **取 [解壓縮至** ] 欄位下方的核取方塊。
* 選取 [確定]。

### <a name="6-install-winutils-windows-only"></a>6. 僅將 Winutils.exe 安裝 (Windows) 

Apache Spark 的 .NET 需要與 Apache Spark 一起安裝 Winutils.exe。 [下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。 然後，將 Winutils.exe 複製到 **C:\bin\spark-3.0.1-bin-hadoop2.7\bin**。

> [!NOTE]
> 如果您使用的是不同版本的 Hadoop （在 Spark 安裝資料夾名稱的結尾加上批註），請選取與您的 Hadoop 版本相容的 [winutils.exe 版本](https://github.com/steveloughran/winutils) 。

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. 設定 DOTNET_WORKER_DIR 並檢查相依性

執行下列其中一個命令來設定 `DOTNET_WORKER_DIR` 環境變數，.net 應用程式會使用此變數來尋找 Apache Spark 的背景工作二進位檔的 .net。 請務必將取代為 `<PATH-DOTNET_WORKER_DIR>` 您下載並解壓縮的目錄 `Microsoft.Spark.Worker` 。 在 Windows 上，請務必在系統管理員模式中執行命令提示字元。

#### <a name="windows"></a>[Windows](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

最後，再次檢查您可以 `dotnet` `java` `spark-shell` 從命令列執行，然後再移至下一節。

## <a name="write-a-net-for-apache-spark-app"></a>撰寫適用於 Apache Spark 的 .NET 應用程式

### <a name="1-create-a-console-app"></a>1. 建立主控台應用程式

在您的命令提示字元或終端機中執行下列命令，以建立新的主控台應用程式：

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

此 `dotnet` 命令 `new` 會為您建立類型的應用程式 `console` 。 `-o`參數會建立名為 *MySparkApp* 的目錄，您的應用程式會儲存在此目錄中，並填入必要的檔案。 此 `cd MySparkApp` 命令會將目錄變更為您所建立的應用程式目錄。

### <a name="2-install-nuget-package"></a>2. 安裝 NuGet 套件

若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在您的命令提示字元或終端機中，執行下列命令：

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> 除非另有指定，否則本教學課程會使用最新版本的 `Microsoft.Spark` NuGet 套件。

### <a name="3-write-your-app"></a>3. 撰寫您的應用程式

在 Visual Studio Code 或任何文字編輯器中開啟 *Program.cs* ，並以下列程式碼取代所有程式碼：

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

[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) 是 Apache Spark 應用程式的進入點，可管理應用程式的內容和資訊。 使用 [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) 方法時，所指定之檔案中的文字資料 `filePath` 會讀入 [資料框架](xref:Microsoft.Spark.Sql.DataFrame)中。 資料框架是一種將資料組織成一組命名的資料行的方式。 然後，套用一連串的轉換來分割檔案中的句子、將每個字組分組、計算它們，然後以遞減順序排序它們。 這些作業的結果會儲存在另一個資料框架中。 請注意，此時不會執行任何作業，因為 .NET for Apache Spark 會延遲評估資料。 在呼叫 [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) 方法之前，它並不會顯示已 `words` 轉換資料框架至主控台的內容，以執行上述各行中定義的作業。 一旦不再需要 Spark 會話，請使用 [stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) 方法停止您的會話。

### <a name="4-create-data-file"></a>4. 建立資料檔案

您的應用程式會處理包含文字行的檔案。 在 *MySparkApp* 目錄中建立名為 *input.txt* file 的檔案，其中包含下列文字：

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

儲存變更並關閉檔案。

## <a name="run-your-net-for-apache-spark-app"></a>執行適用於 Apache Spark 的 .NET 應用程式

執行下列命令以建立您的應用程式：

```dotnetcli
dotnet build
```

流覽至您的組建輸出目錄，然後使用 `spark-submit` 命令來提交要在 Apache Spark 上執行的應用程式。 請務必以  `<version>` 您的 .net 背景工作版本取代，並以 `<path-of-input.txt>` 您的 *input.txt* 檔案的路徑取代。

### <a name="windows"></a>[Windows](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-3-0_2.12-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-3-0_2.12-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> 此命令假設您已下載 Apache Spark，並將其新增至 PATH 環境變數，以便能夠使用 `spark-submit` 。 否則，您必須使用完整路徑 (例如 *C:\bin\apache-spark\bin\spark-submit* 或 *~/spark/bin/spark-submit*) 。

當您的應用程式執行時，會將 *input.txt* 檔案的字數統計資料寫入主控台。

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

恭喜！ 您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> * 準備適用于 .NET 的環境以進行 Apache Spark
> * 為 Apache Spark 應用程式撰寫您的第一個 .NET
> * 為 Apache Spark 應用程式建立並執行您的 .NET

若要查看說明上述步驟的影片，請參閱 [適用于 Apache Spark 101 影片系列的 .net](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。

若要深入了解，請查看資源頁面。
> [!div class="nextstepaction"]
> [適用於 Apache Spark 的 .NET 資源](../resources/index.md)
