---
title: 開始使用適用于 Apache Spark 的 .NET
description: 探索如何在 Windows 上使用 .NET Core 來執行適用于 Apache Spark 應用程式的 .NET。
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577005"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>教學課程：開始使用適用于 Apache Spark 的 .NET

本教學課程會教您如何在 Windows 上使用 .NET Core 來執行適用于 Apache Spark 應用程式的 .NET。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 準備適用于 .NET 的 Windows 環境以進行 Apache Spark
> * 下載**Microsoft. Spark 背景工作角色**
> * 為 Apache Spark 應用程式建立及執行簡單的 .NET

## <a name="prepare-your-environment"></a>準備您的環境

開始之前, 請確定`dotnet`您可以`spark-shell`從命令列`java`執行`mvn`、、。 如果您的環境已準備就緒, 您可以跳到下一節。 如果您無法執行任何或所有的命令, 請遵循下列步驟。

1. 下載並安裝[.Net Core 2.1 x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)。 安裝 SDK 會將工具鏈`dotnet`新增至您的路徑。 使用 PowerShell 命令`dotnet --version`來確認安裝。

2. 以最新的更新安裝[Visual Studio 2017](https://www.visualstudio.com/downloads/)或[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) 。 您可以使用「社區」、「專業」或「企業」。 「社區」版本是免費的。

   在安裝期間選擇下列工作負載:
      * .NET 桌面開發
          * 所有必要元件
          * .NET Framework 4.6.1 開發工具
      * .NET Core 跨平台開發
          * 所有必要元件

3. 安裝[JAVA 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)。

    * 為您的作業系統選取適當的版本。 例如, 針對 Windows x64 電腦選取**jdk-8u201-windows-x64。**
    * 使用 PowerShell 命令`java -version`來確認安裝。

4. 安裝[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)。
    * 下載[Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip)。
    * 解壓縮至本機目錄。 例如： `c:\bin\apache-maven-3.6.0\` 。
    * 將 Apache Maven 新增至您的[PATH 環境變數](https://www.java.com/en/download/help/path.xml)。 如果您將解壓縮`c:\bin\apache-maven-3.6.0\`至, 您會`c:\bin\apache-maven-3.6.0\bin`將新增至您的路徑。
    * 使用 PowerShell 命令`mvn -version`來確認安裝。

5. 安裝[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)。 不支援 Apache Spark 2.4 +。
    * 下載[Apache Spark 2.3 +](https://spark.apache.org/downloads.html) , 並使用[7-zip](https://www.7-zip.org/)或[WinZip](https://www.winzip.com/)之類的工具將它解壓縮至本機資料夾。 例如, 您可能會將它解壓縮`c:\bin\spark-2.3.2-bin-hadoop2.7\`至。
    * 將 Apache Spark 新增至您的[PATH 環境變數](https://www.java.com/en/download/help/path.xml)。 如果您將解壓縮`c:\bin\spark-2.3.2-bin-hadoop2.7\`至, 您會`c:\bin\spark-2.3.2-bin-hadoop2.7\bin`將新增至您的路徑。
    * 新增名`SPARK_HOME`為的[環境變數](https://www.java.com/en/download/help/path.xml)。 如果您已解壓縮`C:\bin\spark-2.3.2-bin-hadoop2.7\`至, `C:\bin\spark-2.3.2-bin-hadoop2.7\`請使用做為**變數值**。
    * 確認您可以從命令列`spark-shell`執行。

6. 設定[winutils.exe](https://github.com/steveloughran/winutils)。
    * 從[winutils.exe 儲存](https://github.com/steveloughran/winutils)機制下載**winutils.exe**二進位檔。 選取用來編譯 Spark 發佈的 Hadoop 版本。 例如, 您可以使用**hadoop-2.7.1** for **Spark 2.3.2**。 Hadoop 版本會在 Spark 安裝資料夾名稱的結尾加上批註。
    * 將**winutils.exe**儲存至您選擇的目錄。 例如： `c:\hadoop\bin` 。
    * 設定`HADOOP_HOME`為不`bin`使用**winutils.exe**來反映目錄。 例如： `c:\hadoop` 。
    * 設定要包含`%HADOOP_HOME%\bin`的 PATH 環境變數。

再次檢查您是否可以從`dotnet`命令`java`行`mvn`執行`spark-shell` 、、, 再移至下一節。

## <a name="download-the-microsoftsparkworker-release"></a>下載 Microsoft. Spark. Worker 版本

1. 從 .NET for Apache Spark GitHub 版本頁面下載到您的本機電腦上的[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases)版本。 例如, 您可以將它下載到路徑`c:\bin\Microsoft.Spark.Worker\`。

2. 建立名`DotnetWorkerPath`為的[新環境變數](https://www.java.com/en/download/help/path.xml), 並將它設定為您下載並解壓縮的目錄。 例如： `c:\bin\Microsoft.Spark.Worker` 。

## <a name="clone-the-net-for-apache-spark-github-repo"></a>複製適用于 Apache Spark GitHub 存放庫的 .NET

使用下列[GitBash](https://gitforwindows.org/)命令, 將 Apache Spark 存放庫的 .net 複製到您的電腦。

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>撰寫適用于 Apache Spark 應用程式的 .NET

1. 開啟**Visual Studio** , 然後流覽至 檔案 **> 建立新的專案 > 主控台應用程式 (.net Core)** 。 將應用程式命名為**HelloSpark**。

2. 安裝[Microsoft Spark NuGet 套件](https://www.nuget.org/profiles/spark)。 如需有關安裝 NuGet 套件的詳細資訊, 請參閱[安裝 Nuget 套件的不同方式](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package)。

3. 在**方案總管**中, 開啟**Program.cs** , 並撰寫C#下列程式碼:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. 建置方案。

## <a name="run-your-net-for-apache-spark-app"></a>執行適用于 Apache Spark 應用程式的 .NET

1. 開啟**PowerShell** , 並將目錄變更為您的應用程式儲存所在的資料夾。

   ```powershell
   cd <your-app-output-directory>
   ```

2. 使用下列內容建立名為的檔案:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. 使用下列 PowerShell 命令來執行您的應用程式:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

恭喜您！ 您已成功撰寫並執行適用于 Apache Spark 應用程式的 .NET。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 準備適用于 .NET 的 Windows 環境以進行 Apache Spark
> * 下載**Microsoft. Spark 背景工作角色**
> * 為 Apache Spark 應用程式建立及執行簡單的 .NET

若要深入瞭解, 請參閱資源頁面。
> [!div class="nextstepaction"]
> [適用于 Apache Spark 資源的 .NET](../resources/index.md)
