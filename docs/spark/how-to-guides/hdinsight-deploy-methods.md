---
title: 將阿帕奇 Spark 作業的 .NET 提交到 Azure HDInsight
description: 瞭解如何使用火花提交和 Apache Livy 將 Apache Spark 作業提交 .NET 到 Azure HDInsight。
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185790"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>將阿帕奇 Spark 作業的 .NET 提交到 Azure HDInsight

有兩種方法可以將用於 Apache Spark 的 .NET 作業部署到`spark-submit`HDInsight：和 Apache Livy。

## <a name="deploy-using-spark-submit"></a>使用火花提交進行部署

您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。

1. 導航到 Azure 門戶中的 HDInsight Spark 群集，然後選擇**SSH + 群集登錄**。

2. 複製 ssh 登錄資訊並將登錄粘貼到終端中。 使用在群集創建期間設置的密碼登錄到群集。 您應該會看到歡迎您訪問 Ubuntu 和 Spark 的消息。

3. 使用**火花提交**命令在 HDInsight 群集上運行應用。 請記住，在示例腳本中用 blob 容器和存儲帳戶的實際名稱替換**我的容器**和**我的存儲帳戶**。 此外，請確保`microsoft-spark-2.3.x-0.6.0.jar`替換為用於部署的相應 jar 檔。 `2.3.x`表示 Apache Spark 的版本，`0.6.0`表示 Apache Spark 工作人員的[.NET](https://github.com/dotnet/spark/releases)版本。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>使用阿帕奇利維部署

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

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [將 .NET for Apache Spark 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [HDInsight 文檔](https://docs.microsoft.com/azure/hdinsight/)
