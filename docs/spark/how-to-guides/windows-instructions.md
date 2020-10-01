---
title: 針對 Windows 上的 Apache Spark 應用程式建立 .NET
description: 瞭解如何在 Windows 上建立適用于 Apache Spark 應用程式的 .NET。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: d355380e92235e799d366dca02eaf8450f563f33
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609274"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>瞭解如何在 Windows 上建立適用于 Apache Spark 應用程式的 .NET

本文會教您如何在 Windows 上建立適用于 Apache Spark 應用程式的 .NET。

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>先決條件

如果您已經擁有下列所有必要條件，請跳至 [組建](#build) 步驟。

  1. 下載並安裝 **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** -安裝 SDK 會將 `dotnet` 工具鏈新增至您的路徑。 支援 .NET Core 2.1、2.2 和3.1。
  2. 安裝 **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (16.3 版或更新版本) 。 此社區版本完全免費。 設定安裝時，請至少包含下列元件：
     * .NET 桌面開發
       * 所有必要元件
         * .NET Framework 4.6.1 開發工具
     * .NET Core 跨平台開發
       * 所有必要元件
  3. 安裝 **[JAVA 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**。
     - 為您的作業系統選取適當版本。 例如，適用于 Windows x64 電腦的 *jdk-8u201-windows-x64.exe* 。
     - 使用安裝程式進行安裝，並確認您可以 `java` 從命令列執行。
  4. 安裝 **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**。
     - 下載 [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip)。
     - 解壓縮到本機目錄。 例如，* C:\bin\apache-maven-3.6.0 \* 。
     - 將 Apache Maven 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。 例如， *C:\bin\apache-maven-3.6.0\bin*。
     - 確認您可以 `mvn` 從命令列執行。
  5. 安裝 **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**。
     - 下載 [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) ，並將其解壓縮至本機資料夾 (例如， * \* 使用 [7-zip](https://www.7-zip.org/)的 C:\bin\spark-2.3.2-bin-hadoop2.7) 。 (支援的 Spark 版本為 2.3*（2.4.0、2.4.1、2.4.3 和2.4.4）) 
     - [新增環境變數](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` 。 例如，* C:\bin\spark-2.3.2-bin-hadoop2.7 \* 。

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - 將 Apache Spark 新增到您的 [PATH 環境變數](https://www.java.com/en/download/help/path.xml)之中。 例如， *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*。

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - 確認您可以 `spark-shell` 從命令列執行。
        範例主控台輸出：

        ```output
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. 安裝 **[winutils.exe](https://github.com/steveloughran/winutils)**。
     - `winutils.exe`從 winutils.exe 存放[庫](https://github.com/steveloughran/winutils)下載二進位檔。 您應該選取用來編譯 Spark 散發套件的 Hadoop 版本。 針對 exammple，請針對 Spark 2.3.2 使用 hadoop-2.7.1。
     - 將 `winutils.exe` 二進位檔儲存至您選擇的目錄。 例如， *C:\hadoop\bin*。
     - 設定 `HADOOP_HOME` 為以不含 bin) 的 winutils.exe (來反映目錄。 例如，使用命令列：

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - 設定要包含的 PATH 環境變數 `%HADOOP_HOME%\bin` 。 例如，使用命令列：

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

`dotnet` `java` `mvn` `spark-shell` 在移至下一節之前，請先確定您能夠從命令列執行。 覺得有更好的方法？ [開啟問題](https://github.com/dotnet/spark/issues) ，並歡迎您提供貢獻。

> [!NOTE]
> 如果已更新任何環境變數，則可能需要新的命令列實例。

## <a name="build"></a>組建

針對本指南的其餘部分，您必須將 Apache Spark 存放庫的 .NET 複製到您的電腦。 您可以為複製的存放庫選擇任何位置。 例如，* C:\github\dotnet-spark \* 。

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>針對 Apache Spark Scala 擴充功能層建立 .NET

當您提交 .NET 應用程式時，適用于 Apache Spark 的 .NET 具有以 Scala 撰寫的必要邏輯，以通知 Apache Spark 如何處理您的要求 (例如，要求建立新的 Spark 會話、要求將資料從 .NET 端傳輸至 JVM 端等。 ) 。 您可以在適用于 Spark 的 [.Net Scala 原始程式碼](https://github.com/dotnet/spark/tree/master/src/scala)中找到此邏輯。

無論您是使用 .NET Framework 或 .NET Core，都必須為 Apache Spark Scala 擴充功能層建立 .NET：

```powershell
cd src\scala
mvn clean package
```

您應該會看到針對支援的 Spark 版本所建立的 Jar：

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>建立適用于 Spark 的 .NET 範例應用程式

本節說明如何針對 Apache Spark 建立適用于 .NET 的 [範例應用程式](https://github.com/dotnet/spark/tree/master/examples) 。 這些步驟將有助於瞭解任何適用于 Spark 應用程式之 .NET 的整體建築流程。

#### <a name="using-visual-studio-for-net-framework"></a>針對 .NET Framework 使用 Visual Studio

  1. `src\csharp\Microsoft.Spark.sln`在 Visual Studio 中開啟，並在 `Microsoft.Spark.CSharp.Examples` 資料夾下建立專案 `examples` (這會接著建立 .net 系結專案) 。 如果您想要的話，您可以在專案中撰寫自己的程式碼 `Microsoft.Spark.Examples` input_file.js(在此範例中為 json 檔案，其中包含您想要使用) 建立資料框架的資料：
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     組建成功之後，您會看到輸出目錄中產生的適當二進位檔。
     範例主控台輸出：

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a>使用適用于 .NET Core 的 .NET Core CLI

> [!NOTE]
> 我們目前正在為 Spark .NET 的 .NET Core 組建進行自動化。 在那之前，我們非常感謝您的耐心等候手動執行某些步驟。

  1. 建立背景工作角色：

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      範例主控台輸出：

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. 建立範例：

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      範例主控台輸出：

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a>執行適用于 Spark 的 .NET 範例應用程式

一旦您建立範例之後， `spark-submit` 無論您是以 .NET Framework 或 .Net Core 為目標，執行它們都將會完成。 請確定您已遵循 [必要條件](#prerequisites) 一節並安裝 Apache Spark。

  1. 設定 `DOTNET_WORKER_DIR` 或 `PATH` 環境變數以包含 `Microsoft.Spark.Worker` 已產生二進位檔的路徑 (例如， *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework， *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .net Core) ：

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. 開啟 PowerShell 並移至您的應用程式二進位檔產生所在的目錄 (例如，適用于 .NET Framework 的 *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* 、.net Core) 的 *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* ：

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. 執行應用程式的基本結構如下：

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     以下是您可以執行的一些範例：

     - **[Microsoft.Spark.Examples.Sql.Batch。基本](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[StructuredNetworkWordCount （範例）。](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[StructuredKafkaWordCount (maven 可存取的可存取) ](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[StructuredKafkaWordCount () 提供的 jar 範例。 ](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
