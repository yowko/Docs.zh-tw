---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows 上使用 .NET Core 執行適用於 Apache Spark 的 .NET 應用程式。
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1b736e078eea40e399882c0df020062b6aa758ad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740522"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>教學課程：開始使用適用于 Apache Spark 的 .NET

本教學課程將指導您如何在 Windows 上使用 .NET Core，執行適用於 Apache Spark 的 .NET 應用程式。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 為適用於 Apache Spark 的 .NET 準備您的 Windows 環境
> * 撰寫 Apache Spark 應用程式的第一個 .NET
> * 為 Apache Spark 應用程式建立及執行您的簡單 .NET

## <a name="prepare-your-environment"></a>準備您的環境

開始撰寫應用程式之前，您必須先設定一些必要的相依性。 如果您可以從命令列環境執行 `dotnet`、`java`、`mvn``spark-shell`，則您的環境已準備就緒，您可以跳到下一節。 如果您無法執行任何或所有的命令，請執行下列步驟。

### <a name="1-install-net"></a>1. 安裝 .NET

若要開始建立 .NET 應用程式，您必須下載並安裝 .NET SDK （軟體發展工具組）。

下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0)。 安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。 

安裝 .NET Core SDK 之後，請開啟新的命令提示字元，然後執行 `dotnet`。

如果命令執行並印出有關如何使用 dotnet 的資訊，可以移至下一個步驟。 如果您收到 `'dotnet' is not recognized as an internal or external command` 錯誤，請確定您在執行命令之前，已開啟**新**的命令提示字元。 

### <a name="2-install-java"></a>2. 安裝 JAVA

安裝[JAVA 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)。

為您的作業系統選取適當版本。 例如，為 Windows x64 電腦選取 **jdk-8u201-windows-x64.exe**。 然後，使用命令 `java` 來確認安裝。
   
![JAVA 下載](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a>3. 安裝 7-zip

Apache Spark 會下載為 tgz 檔案。 使用類似 7-zip 的抽取程式來解壓縮檔案。

* 流覽[7-Zip 下載](https://www.7-zip.org/)。
* 在頁面上的第一個表格中，根據您的作業系統選取32位 x86 或64位 x64 下載。
* 當下載完成時，執行安裝程式。
   
![7Zip 下載](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

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
    
執行下列命令，設定用來尋找 Apache Spark 的環境變數：

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

安裝所有專案並設定您的環境變數之後，請開啟**新**的命令提示字元，然後執行下列命令：

`%SPARK_HOME%\bin\spark-submit --version`

如果命令執行並列印版本資訊，您可以移至下一個步驟。

如果您收到 `'spark-submit' is not recognized as an internal or external command` 錯誤，請確定您已開啟**新**的命令提示字元。

### <a name="5-install-net-for-apache-spark"></a>5. 安裝適用于 Apache Spark 的 .NET

從適用于 Apache Spark GitHub 的 .NET 下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases)版本。 例如，如果您是在 Windows 電腦上，並打算使用 .NET Core，請[下載 windows x64 netcoreapp 2.1 版](https://github.com/dotnet/spark/releases/download/v0.5.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip)。

若要解壓縮 Microsoft. Spark. Worker：

* 找出您下載的**netcoreapp 2.1. win-x64-0.6.0 .zip**檔案。
* 按一下滑鼠右鍵，然後選取 [ **7-Zip-> 解壓縮檔**案 ...]。
* 在 [**解壓縮至**] 欄位中，輸入**C:\bin** 。
* 取消核**取 [解壓縮至**] 欄位下方的核取方塊。
* 選取 [確定]。
  
![安裝 .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a>6. 安裝 Winutils.exe

適用于 Apache Spark 的 .NET 需要與 Apache Spark 一起安裝 Winutils.exe。 [下載 winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe)。 然後，將 Winutils.exe 複製到**C:\bin\spark-2.4.1-bin-hadoop2.7\bin**。

> [!NOTE]
> 如果您使用的是不同版本的 Hadoop （在 Spark 安裝資料夾名稱的結尾加上批註），請選取與您的 Hadoop 版本相容的[winutils.exe 版本](https://github.com/steveloughran/winutils)。 

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. 設定 DOTNET_WORKER_DIR 並檢查相依性

執行下列命令來設定 `DOTNET_WORKER_DIR` 環境變數，以供 .NET 應用程式用來找出適用于 Apache Spark 的 .NET：

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

最後，再次檢查您可以從命令列執行 `dotnet`、`java`、`mvn``spark-shell`，然後再移到下一節。

## <a name="write-a-net-for-apache-spark-app"></a>撰寫適用於 Apache Spark 的 .NET 應用程式

### <a name="1-create-a-console-app"></a>1. 建立主控台應用程式

在命令提示字元中，執行下列命令以建立新的主控台應用程式：

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

`dotnet` 命令會為您建立類型為 `console` 的 `new` 應用程式。 `-o` 參數會建立名為*mySparkApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。 `cd mySparkApp` 命令會將目錄變更為您剛才建立的應用程式目錄。

### <a name="2-install-nuget-package"></a>2. 安裝 NuGet 套件

若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在命令提示字元中，執行下列命令：

`dotnet add package Microsoft.Spark --version 0.6.0`

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

### <a name="4-add-data-file"></a>4. 加入資料檔案

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

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. 當您的應用程式執行時，會將*輸入 .txt*檔案的字數統計資料寫入主控台。

恭喜您！ 您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 為適用於 Apache Spark 的 .NET 準備您的 Windows 環境
> * 撰寫 Apache Spark 應用程式的第一個 .NET
> * 為 Apache Spark 應用程式建立及執行您的簡單 .NET

若要觀看說明上述步驟的影片，請參閱[適用于 Apache Spark 101 的 .net 影片系列](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)。

若要深入了解，請查看資源頁面。
> [!div class="nextstepaction"]
> [適用於 Apache Spark 的 .NET 資源](../resources/index.md)
