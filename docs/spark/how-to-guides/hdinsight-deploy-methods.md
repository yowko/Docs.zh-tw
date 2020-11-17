---
title: 提交 Apache Spark 作業的 .NET 以 Azure HDInsight
description: 瞭解如何提交 Apache Spark 作業的 .NET，以使用 Spark 提交和 Apache Livy Azure HDInsight。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 74be4ecf33a9a881633da0630fa1c1a4bf0b19c6
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688159"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="916eb-103">提交 Apache Spark 作業的 .NET 以 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="916eb-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="916eb-104">有兩種方式可將 Apache Spark 作業的 .NET 部署至 HDInsight： `spark-submit` 和 Apache Livy。</span><span class="sxs-lookup"><span data-stu-id="916eb-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="916eb-105">使用 spark 部署-提交</span><span class="sxs-lookup"><span data-stu-id="916eb-105">Deploy using spark-submit</span></span>

<span data-ttu-id="916eb-106">您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="916eb-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="916eb-107">在 Azure 入口網站中流覽至您的 HDInsight Spark 叢集，然後選取 **[SSH + 叢集登** 入]。</span><span class="sxs-lookup"><span data-stu-id="916eb-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="916eb-108">複製 ssh 登入資訊，並將登入貼到終端機。</span><span class="sxs-lookup"><span data-stu-id="916eb-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="916eb-109">使用您在叢集建立期間設定的密碼來登入您的叢集。</span><span class="sxs-lookup"><span data-stu-id="916eb-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="916eb-110">您應該會看到歡迎您前往 Ubuntu 和 Spark 的訊息。</span><span class="sxs-lookup"><span data-stu-id="916eb-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="916eb-111">使用 **spark 提交** 命令，在您的 HDInsight 叢集上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="916eb-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="916eb-112">請記得將範例腳本中的 **mycontainer** 和 **mystorageaccount** 取代為 blob 容器和儲存體帳戶的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="916eb-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="916eb-113">也請記得將 microsoft spark jar 取代為要使用 Apache Spark 的 Spark 和 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="916eb-113">Also remember to replace the microsoft-spark jar with the version of Spark and .NET for Apache Spark being used.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="916eb-114">使用 Apache Livy 進行部署</span><span class="sxs-lookup"><span data-stu-id="916eb-114">Deploy using Apache Livy</span></span>

<span data-ttu-id="916eb-115">您可以使用 [Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) 來將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight Spark 叢集。</span><span class="sxs-lookup"><span data-stu-id="916eb-115">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="916eb-116">如需詳細資訊，請參閱 [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface) (使用 Apache Livy 的遠端作業)。</span><span class="sxs-lookup"><span data-stu-id="916eb-116">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="916eb-117">您可以使用 `curl`，在 Linux 上執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="916eb-117">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="916eb-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="916eb-118">Next steps</span></span>

* [<span data-ttu-id="916eb-119">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="916eb-119">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="916eb-120">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="916eb-120">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="916eb-121">HDInsight 檔</span><span class="sxs-lookup"><span data-stu-id="916eb-121">HDInsight Documentation</span></span>](/azure/hdinsight/)
