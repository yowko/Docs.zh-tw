---
title: 將適用于 Apache Spark 作業的 .NET 提交至 Azure HDInsight
description: 瞭解如何使用 Spark-submit 和 Apache Livy，將 Apache Spark 作業的 .NET 提交至 Azure HDInsight。
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: cdd5e15ffde78ccb8b3156ee047b8ca98f7320b8
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74553008"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>將適用于 Apache Spark 作業的 .NET 提交至 Azure HDInsight

有兩種方式可將適用于 Apache Spark 作業的 .NET 部署至 HDInsight： `spark-submit` 和 Apache Livy。

## <a name="deploy-using-spark-submit"></a>使用 spark 部署-提交

您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。
 
1. 在 Azure 入口網站中，流覽至您的 HDInsight Spark 叢集，然後選取 **[SSH + 叢集登**入]。

2. 複製 ssh 登入資訊，並將登入貼入終端機。 使用您在叢集建立期間所設定的密碼來登入您的叢集。 您應該會看到歡迎您前往 Ubuntu 和 Spark 的訊息。

3. 使用**spark-submit**命令在 HDInsight 叢集上執行您的應用程式。 請記得以您的 blob 容器和儲存體帳戶的實際名稱取代範例腳本中的**mycontainer**和**mystorageaccount** 。 此外，請務必將 `microsoft-spark-2.3.x-0.6.0.jar` 取代為您要用於部署的適當 jar 檔案。 `2.3.x` 代表 Apache Spark 的版本，而 `0.6.0` 則代表[Apache Spark worker 的 .net](https://github.com/dotnet/spark/releases)版本。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>使用 Apache Livy 進行部署

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

* [開始使用適用於 Apache Spark 的 .NET](../tutorials/get-started.md)
* [將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight 檔](https://docs.microsoft.com/azure/hdinsight/)
