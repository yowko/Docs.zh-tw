---
title: 針對 Apache Spark 背景工作角色和使用者定義函數二進位檔部署 .NET
description: 瞭解如何為 Apache Spark 背景工作角色和使用者定義函數二進位檔部署 .NET。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c777fdb26045c62317b49259fdde974f43ba5c0d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293763"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>針對 Apache Spark 背景工作角色和使用者定義函數二進位檔部署 .NET

本 how to 提供有關如何為 Apache Spark 背景工作角色和使用者定義的函式二進位檔部署 .NET 的一般指示。 您將瞭解要設定的環境變數，以及用來啟動應用程式的一些常用參數 `spark-submit` 。

## <a name="configurations"></a>組態

設定會顯示一般環境變數和參數設定，以針對 Apache Spark 背景工作角色和使用者定義函數二進位檔部署 .NET。

### <a name="environment-variables"></a>環境變數

部署背景工作和寫入 Udf 時，您可能需要設定一些常用的環境變數：

| 環境變數         | 描述
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | <code>Microsoft.Spark.Worker</code>已產生二進位檔的路徑。</br>它是由 Spark 驅動程式使用，並會傳遞給 Spark 執行程式。 如果未設定此變數，Spark 執行程式會搜尋環境變數中指定的路徑 <code>PATH</code> 。</br>_例如 "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | 以逗號分隔的路徑，其中 <code>Microsoft.Spark.Worker</code> 會載入元件。</br>請注意，如果路徑的開頭為 "."，則會在前面加上工作目錄。 如果在 **yarn 模式** 中，"." 會代表容器的工作目錄。</br>_例如 "C:\Users \\ &lt; user name &gt; \\ &lt; mysparkapp &gt; \bin\Debug \\ &lt; dotnet version &gt; "_
| DOTNET_WORKER_DEBUG          | 如果您想要對 <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF 進行 debug</a>，請在執行之前將此環境變數設定為 <code>1</code> <code>spark-submit</code> 。

### <a name="parameter-options"></a>參數選項

一旦將 Spark 應用程式 [配套](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)之後，您就可以使用來啟動它 `spark-submit` 。 下表顯示一些常用的選項：

| 參數名稱        | 描述
| :---------------------| :----------
| --類別               | 您應用程式的進入點。</br>_例如，dotnet. DotnetRunner。_
| --master              | 叢集的 <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">主要 URL</a> 。</br>_例如 yarn_
| --部署模式         | 是否要在背景工作節點上部署您的驅動程式 (<code>cluster</code>) ，或在本機作為外部用戶端 (<code>client</code>) 。</br>預設： <code>client</code>
| --會議                | 格式的任意 Spark <code>key=value</code> 設定屬性。</br>_例如 spark.yarn.appMasterEnv.DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --files               | 要放在每個執行程式工作目錄中的檔案清單（以逗號分隔）。<br/><ul><li>請注意，此選項僅適用于 yarn 模式。</li><li>它支援指定具有類似于 Hadoop 的 # 檔案名。</br></ul>_例如 <code>myLocalSparkApp.dll#appSeen.dll</code> ：在 YARN 上執行時，您的應用程式應該使用名稱做為 <code>appSeen.dll</code> 參考 <code>myLocalSparkApp.dll</code> 。_</li>
| --封存          | 要解壓縮到每個執行程式工作目錄中的封存清單（以逗號分隔）。</br><ul><li>請注意，此選項僅適用于 yarn 模式。</li><li>它支援指定具有類似于 Hadoop 的 # 檔案名。</br></ul>_例如 <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> ：這會將 zip 檔案複製並解壓縮至 <code>worker</code> 資料夾。_</li>
| 應用程式-jar       | 配套的 jar 路徑，包括您的應用程式和所有相依性。</br>_例如 &lt; ，jar &gt; /microsoft-spark- &lt; 版本 &gt; .jar 的 hdfs://路徑_
| 應用程式-引數 | 傳遞至主要類別之 main 方法的引數（如果有的話）。</br>_例如，應用程式的 hdfs:// &lt; 路徑 &gt; / &lt; &gt; 。 .zip 您的應用程式 &lt; 名稱 &gt; &lt; 應用程式引數&gt;_

> [!NOTE]
> `--options` `application-jar` 使用啟動應用程式時，請指定所有的 `spark-submit` ，否則會忽略它們。 如需詳細資訊，請參閱 YARN 上的[ `spark-submit` 選項](https://spark.apache.org/docs/latest/submitting-applications.html)和執行[spark 詳細資料](https://spark.apache.org/docs/latest/running-on-yarn.html)。

## <a name="frequently-asked-questions"></a>常見問題集

### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>當我執行具有 Udf 的 spark 應用程式時，我收到「FileNotFoundException」錯誤。 我該怎麼辦？

> **錯誤：** [錯誤] [TaskRunner] [0] ProcessStream ( # A1 失敗，例外狀況：： Assembly ' MySparkApp，Version = 1.0.0.0，Culture = 中性，PublicKeyToken = null ' 找不到檔案： ' mySparkApp.dll '

**答：** 檢查是否 `DOTNET_ASSEMBLY_SEARCH_PATHS` 已正確設定環境變數。 它應該是包含的路徑 `mySparkApp.dll` 。

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>在升級 Apache Spark 版本的 .NET 並重設 `DOTNET_WORKER_DIR` 環境變數之後，為什麼仍會收到下列 `IOException` 錯誤？

> **錯誤：** 在階段11.0 中遺失工作 0.0 (TID 24、localhost、執行程式驅動程式) ： IOException：無法執行程式 "Microsoft.Spark.Worker.exe"： CreateProcess error = 2，系統找不到指定的檔案。

**答：** 請先嘗試重新開機 PowerShell 視窗 (或其他命令視窗) ，讓它可以採用最新的環境變數值。 然後啟動您的程式。

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>提交 Spark 應用程式之後，我收到錯誤訊息 `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'` 。

> **錯誤：** [錯誤] [TaskRunner] [0] ProcessStream ( # A1 失敗，例外狀況： TypeLoadException：無法從元件 ' Mscorlib.dll，Version = 4.0.0.0，Culture = 中立，PublicKeyToken = ... ' 載入類型 ' '。

**答：** 檢查 `Microsoft.Spark.Worker` 您正在使用的版本。 有兩個版本： **.NET Framework 4.6.1** 和 **.net Core 3.1. x**。 在此情況下， `Microsoft.Spark.Worker.net461.win-x64-<version>` 您可以 [下載](https://github.com/dotnet/spark/releases))  (，因為 `System.Runtime.Remoting.Contexts.Context` 只適用于 .NET Framework。

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>如何? 在 YARN 上執行具有 Udf 的 spark 應用程式？ 我應該使用哪些環境變數和參數？

**答：** 若要在 YARN 上啟動 spark 應用程式，應將環境變數指定為 `spark.yarn.appMasterEnv.[EnvironmentVariableName]` 。 請參閱下面的範例，以瞭解如何使用 `spark-submit` ：

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>下一步

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯](debug.md)
