---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 HDInsight。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9da0e0fd83d70887109c63a5e95ec0b0b31a2edd
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928475"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight

本教學課程會教導如何將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 準備 Microsoft.Spark.Worker
> * 發佈您的 Spark .NET 應用程式
> * 將您的應用程式部署到 Azure HDInsight
> * 執行應用程式

## <a name="prerequisites"></a>必要條件

開始之前，請執行下列動作：

* 下載 [Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)。
* 將 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下載到您的本機電腦。 這是您稍後用來將適用於 Apache Spark 的 .NET 應用程式相依檔案複製到您 Spark 叢集背景工作節點的協助程式指令碼。

## <a name="prepare-worker-dependencies"></a>準備背景工作相依性

**Microsoft.Spark.Worker** 是一種後端元件，其存在於您 Spark 叢集的個別背景工作節點上。 當您想要執行 C# UDF (使用者定義函式) 時，Spark 需要了解如何啟動 .NET CLR 來執行 UDF。 **Microsoft.Spark.Worker** 會向 Spark 提供類別集合，其會啟用此功能。

1. 選取要部署在您叢集上的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。

   例如，若您想要使用 `netcoreapp2.1` 的 `.NET for Apache Spark v0.1.0`，您可以下載 [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)。

2. 將 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上傳到您叢集可以存取的分散式檔案系統 (例如 HDFS、WASB、ADLS)。

## <a name="prepare-your-net-for-apache-spark-app"></a>準備適用於 Apache Spark 的 .NET 應用程式

1. 遵循[開始使用](get-started.md)教學課程來建置您的應用程式。

2. 將您的 Spark .NET 應用程式發佈為獨立式應用程式。

   您可以在 Linux 上執行下列命令。

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. 為發佈的檔案產生 `<your app>.zip`。

   您可以使用 `zip`，在 Linux 上執行下列命令。

   ```bash
   zip -r <your app>.zip .
   ```

4. 將下列項目上傳到您叢集可存取的分散式檔案系統 (例如 HDFS、WASB、ADLS)：

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`：此 jar 已作為 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件的一部分包含在其中，且已共置於您應用程式的建置輸出目錄。
   * `<your app>.zip`
   * 要放在每個執行程式中工作目錄的檔案 (例如相依性檔案或每個背景工作都可存取的通用資料) 或組件 (例如包含您使用者定義函式或您 `app` 相依程式庫的 DLL)。

## <a name="deploy-to-azure-hdinsight-spark"></a>部署至 Azure HDInsight Spark

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) 是 Microsoft 在雲端中的 Apache Spark 實作，可讓使用者在 Azure 中啟動和設定 Spark 叢集。 您可以使用 HDInsight Spark 叢集來處理您儲存在 [Azure 儲存體](https://azure.microsoft.com/services/storage/)或 [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2) 中的資料。

> [!NOTE]
> Azure HDInsight Spark 是以 Linux 為基礎。 若您想要將應用程式部署到 Azure HDInsight Spark，請確認應用程式與 .NET Standard 相容，且您是使用 [.NET Core 編譯器](https://dotnet.microsoft.com/download)來編譯應用程式。

### <a name="deploy-microsoftsparkworker"></a>部署 Microsoft.Spark.Worker

針對您的叢集，此步驟只需要一次。

使用 [HDInsight 指令碼動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-worker.sh`。

|設定|值|
|-------|-----|
|腳本類型|自訂|
|名稱|安裝 Microsoft.Spark.Worker|
|Bash 腳本 URI|您上傳 `install-worker.sh` 的目標 URI。 例如： `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|節點類型|工作|
|參數|`install-worker.sh` 的參數。 例如，若您將 `install-worker.sh` 上傳到 Azure Data Lake Gen 2，它便會是 `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`。|

![指令碼動作影像](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>執行應用程式

您可以使用 `spark-submit` 或 Apache Livy 將作業提交到 Azure HDInsight。

### <a name="use-spark-submit"></a>使用 spark-submit

您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。
 
1. `ssh` 到您叢集中的其中一個前端節點。

1. 執行`spark-submit`：

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>使用 Apache Livy

您可以使用 [Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) 來將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight Spark 叢集。 如需詳細資訊，請參閱 [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface) (使用 Apache Livy 的遠端作業)。

您可以使用 `curl`，在 Linux 上執行下列命令：

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。 若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。

> [!div class="nextstepaction"]
> [Azure HDInsight 檔](https://docs.microsoft.com/azure/hdinsight/)
