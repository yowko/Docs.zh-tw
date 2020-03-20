---
title: 部署 .NET 用於 Apache Spark 工作人員和使用者定義的函數二進位檔案
description: 瞭解如何為 Apache Spark 工作人員和使用者定義的函數二進位檔案部署 .NET。
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f373ccee398149adcadeac91f02d9896214706b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187601"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>部署 .NET 用於 Apache Spark 工作人員和使用者定義的函數二進位檔案

此操作器提供有關如何部署 Apache Spark 工作人員和使用者定義的函數二進位檔案的 .NET 的一般說明。 您將瞭解要設置的環境變數，以及用於使用`spark-submit`啟動應用程式的一些常用參數。

## <a name="configurations"></a>組態
配置顯示常規環境變數和參數設置，以便部署用於 Apache Spark 工作人員和使用者定義的函數二進位檔案.

### <a name="environment-variables"></a>環境變數
在部署輔助工作和編寫 UDF 時，可能需要設置一些常用的環境變數：

| 環境變數         | 描述
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | 生成二進位<code>Microsoft.Spark.Worker</code>檔的路徑。</br>它由 Spark 驅動程式使用，並將傳遞給 Spark 執行器。 如果未設置此變數，Spark 執行器將搜索<code>PATH</code>環境變數中指定的路徑。</br>_例如"C：\bin\微軟.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | 將載入程式集的<code>Microsoft.Spark.Worker</code>Comma 分隔路徑。</br>請注意，如果路徑以"."開頭，則工作目錄將預告。 如果在**紗線模式下**，"."表示容器的工作目錄。</br>_\\ &lt;例如"C：\使用者使用者名&gt;\\&lt;mysparkapp&gt;\bin_調試\\&lt;點網版本"&gt;_
| DOTNET_WORKER_DEBUG          | 如果要<a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">調試 UDF，</a>則在運行<code>1</code><code>spark-submit</code>之前將此環境變數設置為 。

### <a name="parameter-options"></a>參數選項
捆綁 Spark 應用程式[後，](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)可以使用 啟動它`spark-submit`。 下表顯示了一些常用選項：

| 參數名稱        | 描述
| :---------------------| :----------
| --類               | 應用程式的進入點。</br>_例如 org.apache.spark.deploy.dotnet.DotnetRunner_
| --大師              | 群集<a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">的主 URL。</a></br>_例如紗線_
| --部署模式         | 是將驅動程式部署到輔助節點 （<code>cluster</code>） 上，還是將驅動程式部署在本地<code>client</code>作為外部用戶端 （）。</br>預設：<code>client</code>
| --conf                | 格式的<code>key=value</code>任意 Spark 配置屬性。</br>_例如 spark.yarn.appMasterEnv.DOTNET_WORKER_DIR_worker_Microsoft.Spark.Worker_
| --檔               | 要放置在每個執行器的工作目錄中的檔的 Comma 分隔清單。<br/><ul><li>請注意，此選項僅適用于紗線模式。</li><li>它支援使用與 Hadoop 類似的 # 指定檔案名。</br></ul>_例如<code>myLocalSparkApp.dll#appSeen.dll</code>. . . .在 YARN 上運行時，<code>appSeen.dll</code>應用程式應<code>myLocalSparkApp.dll</code>使用該名稱作為引用。_</li>
| --檔案          | 要提取到每個執行器的工作目錄中的由逗號分隔的存檔清單。</br><ul><li>請注意，此選項僅適用于紗線模式。</li><li>它支援使用與 Hadoop 類似的 # 指定檔案名。</br></ul>_例如<code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. . . .這將複製 ZIP 檔案並將其提取到<code>worker</code>資料夾中。_</li>
| 應用程式 jar       | 捆綁的 jar 的路徑，包括應用程式和所有依賴項。</br>_hdfs://&lt;路徑到您的罐子&gt;/微軟火花&lt;版本&gt;.jar_
| 應用程式參數 | 參數傳遞給主類的主方法（如果有）。</br>_&lt;例如，hdfs://應用路徑&gt;/&lt;&gt;.zip&lt;你的應用名稱&gt;&lt;應用 args&gt;_

> [!NOTE]
> 使用 啟動`--options`應用程式`application-jar``spark-submit`時指定所有之前，否則將忽略它們。 有關詳細資訊，請參閱[`spark-submit`](https://spark.apache.org/docs/latest/submitting-applications.html)有關 YARN[詳細資訊的選項和運行火花](https://spark.apache.org/docs/latest/running-on-yarn.html)。

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>當我使用 UF 運行火花應用時，我收到一個"FileNotFoundException"錯誤。 我該怎麼辦？
> **錯誤：** [錯誤] [任務運行者] [0] 進程流（） 失敗，但出現異常：System.IO.fileNotfoundException：程式集'mySparkApp，版本=1.0.0.0，區域性=中立，公共金鑰權杖_null'檔未找到："mySparkApp.dll"

**答案：** 檢查`DOTNET_ASSEMBLY_SEARCH_PATHS`環境變數是否設置正確。 它應該是包含 您的`mySparkApp.dll`的路徑。

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>升級了 Apache Spark 版本的 .NET 並`DOTNET_WORKER_DIR`重置了環境變數後，為什麼我仍然會收到`IOException`以下錯誤？
> **錯誤：** 階段 11.0 中丟失的任務 0.0（TID 24，本地主機，執行器驅動程式）：java.io.IOException： 無法運行程式"Microsoft.Spark.Worker.exe"：創建進程錯誤=2，系統找不到指定的檔。

**答案：** 嘗試首先重新開機 PowerShell 視窗（或其他命令視窗），以便它可以採取最新的環境變數值。 然後啟動程式。

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>提交我的 Spark 應用程式後，我得到錯誤`System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`。
> **錯誤：** [錯誤] [任務運行者] [0] 進程流（） 失敗，但出現異常：System.TypeLoadException：無法載入程式集中的"系統.運行時.Remoting.CoNtext.CoNtext.CoNtext"來自程式集"mscorlib，版本=4.0.0.0，區域性=中性，PublicKeyToken_..."。

**答案：** 檢查正在`Microsoft.Spark.Worker`使用的版本。 有兩個版本 **：.NET 框架 4.6.1**和 **.NET 核心 2.1.x**。 在這種情況下，`Microsoft.Spark.Worker.net461.win-x64-<version>`應使用 （您可以[下載](https://github.com/dotnet/spark/releases)），因為`System.Runtime.Remoting.Contexts.Context`僅用於 .NET 框架。

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>如何在 YARN 上使用 UF 運行火花應用程式？ 我應該使用哪些環境變數和參數？

**答案：** 要在 YARN 上啟動火花應用程式，環境變數應指定為`spark.yarn.appMasterEnv.[EnvironmentVariableName]`。 請參閱下面的示例， 使用`spark-submit`：

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯](../how-to-guides/debug.md)
