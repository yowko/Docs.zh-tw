---
title: 提交 Apache Spark 作業的 .NET 以 Azure HDInsight
description: 瞭解如何提交 Apache Spark 作業的 .NET，以使用 Spark 提交和 Apache Livy Azure HDInsight。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 560822783b57b2419595cb15efa097591db8d600
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557160"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>提交 Apache Spark 作業的 .NET 以 Azure HDInsight

有兩種方式可將 Apache Spark 作業的 .NET 部署至 HDInsight： `spark-submit` 和 Apache Livy。

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a>使用 spark 部署-提交

您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。

1. 在 Azure 入口網站中流覽至您的 HDInsight Spark 叢集，然後選取 **[SSH + 叢集登**入]。

2. 複製 ssh 登入資訊，並將登入貼到終端機。 使用您在叢集建立期間設定的密碼來登入您的叢集。 您應該會看到歡迎您前往 Ubuntu 和 Spark 的訊息。

3. 使用 **spark 提交** 命令，在您的 HDInsight 叢集上執行您的應用程式。 請記得將範例腳本中的 **mycontainer** 和 **mystorageaccount** 取代為 blob 容器和儲存體帳戶的實際名稱。 此外，請務必使用 `microsoft-spark-2.3.x-0.6.0.jar` 您用於部署的適當 jar 檔案來取代。 `2.3.x` 代表 Apache Spark 的版本，並 `0.6.0` 代表 [Apache Spark worker 的 .net](https://github.com/dotnet/spark/releases)版本。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>使用 Apache Livy 進行部署

您可以使用 [Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) 來將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight Spark 叢集。 如需詳細資訊，請參閱 [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface) (使用 Apache Livy 的遠端作業)。

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

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [將 .NET for Apache Spark 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight 檔](/azure/hdinsight/)
