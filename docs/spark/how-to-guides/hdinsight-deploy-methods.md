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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="52937-103">將阿帕奇 Spark 作業的 .NET 提交到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="52937-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="52937-104">有兩種方法可以將用於 Apache Spark 的 .NET 作業部署到`spark-submit`HDInsight：和 Apache Livy。</span><span class="sxs-lookup"><span data-stu-id="52937-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="52937-105">使用火花提交進行部署</span><span class="sxs-lookup"><span data-stu-id="52937-105">Deploy using spark-submit</span></span>

<span data-ttu-id="52937-106">您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="52937-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="52937-107">導航到 Azure 門戶中的 HDInsight Spark 群集，然後選擇**SSH + 群集登錄**。</span><span class="sxs-lookup"><span data-stu-id="52937-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="52937-108">複製 ssh 登錄資訊並將登錄粘貼到終端中。</span><span class="sxs-lookup"><span data-stu-id="52937-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="52937-109">使用在群集創建期間設置的密碼登錄到群集。</span><span class="sxs-lookup"><span data-stu-id="52937-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="52937-110">您應該會看到歡迎您訪問 Ubuntu 和 Spark 的消息。</span><span class="sxs-lookup"><span data-stu-id="52937-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="52937-111">使用**火花提交**命令在 HDInsight 群集上運行應用。</span><span class="sxs-lookup"><span data-stu-id="52937-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="52937-112">請記住，在示例腳本中用 blob 容器和存儲帳戶的實際名稱替換**我的容器**和**我的存儲帳戶**。</span><span class="sxs-lookup"><span data-stu-id="52937-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="52937-113">此外，請確保`microsoft-spark-2.3.x-0.6.0.jar`替換為用於部署的相應 jar 檔。</span><span class="sxs-lookup"><span data-stu-id="52937-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="52937-114">`2.3.x`表示 Apache Spark 的版本，`0.6.0`表示 Apache Spark 工作人員的[.NET](https://github.com/dotnet/spark/releases)版本。</span><span class="sxs-lookup"><span data-stu-id="52937-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="52937-115">使用阿帕奇利維部署</span><span class="sxs-lookup"><span data-stu-id="52937-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="52937-116">您可以使用 [Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) 來將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight Spark 叢集。</span><span class="sxs-lookup"><span data-stu-id="52937-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="52937-117">如需詳細資訊，請參閱 [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface) (使用 Apache Livy 的遠端作業)。</span><span class="sxs-lookup"><span data-stu-id="52937-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="52937-118">您可以使用 `curl`，在 Linux 上執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="52937-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="52937-119">後續步驟</span><span class="sxs-lookup"><span data-stu-id="52937-119">Next steps</span></span>

* [<span data-ttu-id="52937-120">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="52937-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="52937-121">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="52937-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="52937-122">HDInsight 文檔</span><span class="sxs-lookup"><span data-stu-id="52937-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
