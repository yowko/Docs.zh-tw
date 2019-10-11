---
title: 開始使用適用於 Apache Spark 的 .NET
description: 探索如何在 Windows 上使用 .NET Core 執行適用於 Apache Spark 的 .NET 應用程式。
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c4dbce74d0d8c0a682250a8021d983ef2990971f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250317"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>教學課程：開始使用適用於 Apache Spark 的 .NET

本教學課程將指導您如何在 Windows 上使用 .NET Core，執行適用於 Apache Spark 的 .NET 應用程式。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 為適用於 Apache Spark 的 .NET 準備您的 Windows 環境
> * 下載 **Microsoft.Spark.Worker**
> * 建置及執行適用於 Apache Spark 的 .NET 簡單應用程式

## <a name="prepare-your-environment"></a>準備您的環境

開始前，請確認您可以從命令列執行 `dotnet`、`java`、`mvn` 和 `spark-shell`。 當您的環境準備就緒之後，請跳到下一節。 若您無法執行任何或所有的命令，請遵循下列步驟。

1. 下載並安裝 [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)。 安裝 SDK 會將 `dotnet` 工具鏈新增到您的 PATH 之中。 使用 PowerShell 命令 `dotnet --version` 驗證安裝。

2. 安裝包含最新更新的 [Visual Studio 2017](https://www.visualstudio.com/downloads/) 或 [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/)。 您可以使用 Community、Professional 或 Enterprise。 Community 版本免費。

   請在安裝期間選擇下列工作負載：
      * .NET 桌面開發
          * 所有必要元件
          * .NET Framework 4.6.1 開發工具
      * .NET Core 跨平台開發
          * 所有必要元件

3. 安裝 [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)。

    * 為您的作業系統選取適當版本。 例如，為 Windows x64 電腦選取 **jdk-8u201-windows-x64.exe**。
    * 使用 PowerShell 命令 `java -version` 驗證安裝。

4. 安裝 [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)。
    * 下載 [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip)。
    * 解壓縮到本機目錄。 例如，`c:\bin\apache-maven-3.6.0\`。
    * 將 Apache Maven 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。 若解壓縮到 `c:\bin\apache-maven-3.6.0\`，就應將 `c:\bin\apache-maven-3.6.0\bin` 新增到您的 PATH 之中。
    * 使用 PowerShell 命令 `mvn -version` 驗證安裝。

5. 安裝 [Apache Spark 2.3+](https://spark.apache.org/downloads.html)。 不支援 Apache Spark 2.4+。
    * 下載 [Apache Spark 2.3+](https://spark.apache.org/downloads.html)，然後使用 [7-zip](https://www.7-zip.org/) 或 [WinZip](https://www.winzip.com/) 等工具，將其解壓縮到本機資料夾。 例如，您可以將其解壓縮到 `c:\bin\spark-2.3.2-bin-hadoop2.7\`。
    * 將 Apache Spark 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。 若解壓縮到 `c:\bin\spark-2.3.2-bin-hadoop2.7\`，就應將 `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` 新增到您的 PATH 之中。
    * 新增名為 `SPARK_HOME` 的[新環境變數](https://www.java.com/en/download/help/path.xml)。 若解壓縮到 `C:\bin\spark-2.3.2-bin-hadoop2.7\`，請為**變數值**使用 `C:\bin\spark-2.3.2-bin-hadoop2.7\`。
    * 驗證您能夠從命令列執行 `spark-shell`。

6. 設定 [WinUtils](https://github.com/steveloughran/winutils)。
    * 從 [WinUtils 存放庫](https://github.com/steveloughran/winutils)下載 **winutils.exe** 二進位檔。 選取用以編譯 Spark 的 Hadoop 版本。 例如，您可以為 **Spark 2.3.2**使用 **hadoop-2.7.1**。 Hadoop 版本會標註在您 Spark 安裝資料夾名稱的結尾。
    * 將 **winutils.exe** 二進位檔儲存到您選擇的目錄。 例如，`c:\hadoop\bin`。
    * 設定 `HADOOP_HOME` 以反映 **winutils.exe** 的目錄 (不含 `bin`)。 例如，`c:\hadoop`。
    * 設定 PATH 環境變數，將 `%HADOOP_HOME%\bin` 加入其中。

再次確認您可以從命令列執行 `dotnet`、`java`、`mvn` 和 `spark-shell`，然後前往下一節。

## <a name="download-the-microsoftsparkworker-release"></a>下載 Microsoft.Spark.Worker 版本

1. 從適用於 Apache Spark 的 .NET GitHub 版本頁面，將發行的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) 下載到您的本機電腦。 例如，您可以將其下載到 `c:\bin\Microsoft.Spark.Worker\` 路徑。

2. 建立名為 `DOTNET_WORKER_DIR` 的[新環境變數](https://www.java.com/en/download/help/path.xml)，並將其設為 **Microsoft.Spark.Worker** 的下載目錄，然後加以解壓縮。 例如，`c:\bin\Microsoft.Spark.Worker`。

## <a name="clone-the-net-for-apache-spark-github-repo"></a>複製適用於 Apache Spark 的 .NET GitHub 存放庫

使用下列 [GitBash](https://gitforwindows.org/) 命令，將適用於 Apache Spark 的 .NET 存放庫複製到您的電腦。

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>撰寫適用於 Apache Spark 的 .NET 應用程式

1. 開啟 **Visual Studio**，然後巡覽至 [檔案] > [建立新專案] > [主控台應用程式 (.NET Core)]。 將應用程式命名為 **HelloSpark**。

2. 安裝 [Microsoft.Spark NuGet 套件](https://www.nuget.org/profiles/spark)。 如需安裝 NuGet 套件的詳細資訊，請參閱[安裝 NuGet 套件的不同方式](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package)。

3. 在 [方案總管] 中開啟 **Program.cs**，然後撰寫下列 C# 程式碼：

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. 建置方案。

## <a name="run-your-net-for-apache-spark-app"></a>執行適用於 Apache Spark 的 .NET 應用程式

1. 開啟 **PowerShell**，將目錄變更成您應用程式的儲存資料夾。

   ```powershell
   cd <your-app-output-directory>
   ```

2. 建立名為 **people.json** 的檔案，並在其中包含以下內容：

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. 使用下列 PowerShell 命令執行您的應用程式：

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

恭喜您！ 您已成功撰寫及執行適用於 Apache Spark 的 .NET 應用程式。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 為適用於 Apache Spark 的 .NET 準備您的 Windows 環境
> * 下載 **Microsoft.Spark.Worker**
> * 建置及執行適用於 Apache Spark 的 .NET 簡單應用程式

若要深入了解，請查看資源頁面。
> [!div class="nextstepaction"]
> [適用於 Apache Spark 的 .NET 資源](../resources/index.md)
