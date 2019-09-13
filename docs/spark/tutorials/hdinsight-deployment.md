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
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="c97ca-103">將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="c97ca-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="c97ca-104">本教學課程會教導如何將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="c97ca-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="c97ca-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="c97ca-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c97ca-106">準備 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="c97ca-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="c97ca-107">發佈您的 Spark .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ca-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="c97ca-108">將您的應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="c97ca-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="c97ca-109">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ca-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c97ca-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="c97ca-110">Prerequisites</span></span>

<span data-ttu-id="c97ca-111">開始之前，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c97ca-111">Before you start, do the following:</span></span>

* <span data-ttu-id="c97ca-112">下載 [Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)。</span><span class="sxs-lookup"><span data-stu-id="c97ca-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="c97ca-113">將 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下載到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c97ca-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="c97ca-114">這是您稍後用來將適用於 Apache Spark 的 .NET 應用程式相依檔案複製到您 Spark 叢集背景工作節點的協助程式指令碼。</span><span class="sxs-lookup"><span data-stu-id="c97ca-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="c97ca-115">準備背景工作相依性</span><span class="sxs-lookup"><span data-stu-id="c97ca-115">Prepare worker dependencies</span></span>

<span data-ttu-id="c97ca-116">**Microsoft.Spark.Worker** 是一種後端元件，其存在於您 Spark 叢集的個別背景工作節點上。</span><span class="sxs-lookup"><span data-stu-id="c97ca-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="c97ca-117">當您想要執行 C# UDF (使用者定義函式) 時，Spark 需要了解如何啟動 .NET CLR 來執行 UDF。</span><span class="sxs-lookup"><span data-stu-id="c97ca-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="c97ca-118">**Microsoft.Spark.Worker** 會向 Spark 提供類別集合，其會啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="c97ca-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="c97ca-119">選取要部署在您叢集上的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。</span><span class="sxs-lookup"><span data-stu-id="c97ca-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="c97ca-120">例如，若您想要使用 `netcoreapp2.1` 的 `.NET for Apache Spark v0.1.0`，您可以下載 [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="c97ca-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="c97ca-121">將 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上傳到您叢集可以存取的分散式檔案系統 (例如 HDFS、WASB、ADLS)。</span><span class="sxs-lookup"><span data-stu-id="c97ca-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="c97ca-122">準備適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ca-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="c97ca-123">遵循[開始使用](get-started.md)教學課程來建置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ca-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="c97ca-124">將您的 Spark .NET 應用程式發佈為獨立式應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ca-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="c97ca-125">您可以在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c97ca-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="c97ca-126">為發佈的檔案產生 `<your app>.zip`。</span><span class="sxs-lookup"><span data-stu-id="c97ca-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="c97ca-127">您可以使用 `zip`，在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c97ca-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="c97ca-128">將下列項目上傳到您叢集可存取的分散式檔案系統 (例如 HDFS、WASB、ADLS)：</span><span class="sxs-lookup"><span data-stu-id="c97ca-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="c97ca-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`：此 jar 已作為 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件的一部分包含在其中，且已共置於您應用程式的建置輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="c97ca-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="c97ca-130">要放在每個執行程式中工作目錄的檔案 (例如相依性檔案或每個背景工作都可存取的通用資料) 或組件 (例如包含您使用者定義函式或您 `app` 相依程式庫的 DLL)。</span><span class="sxs-lookup"><span data-stu-id="c97ca-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="c97ca-131">部署至 Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="c97ca-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="c97ca-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) 是 Microsoft 在雲端中的 Apache Spark 實作，可讓使用者在 Azure 中啟動和設定 Spark 叢集。</span><span class="sxs-lookup"><span data-stu-id="c97ca-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="c97ca-133">您可以使用 HDInsight Spark 叢集來處理您儲存在 [Azure 儲存體](https://azure.microsoft.com/services/storage/)或 [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2) 中的資料。</span><span class="sxs-lookup"><span data-stu-id="c97ca-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="c97ca-134">Azure HDInsight Spark 是以 Linux 為基礎。</span><span class="sxs-lookup"><span data-stu-id="c97ca-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="c97ca-135">若您想要將應用程式部署到 Azure HDInsight Spark，請確認應用程式與 .NET Standard 相容，且您是使用 [.NET Core 編譯器](https://dotnet.microsoft.com/download)來編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="c97ca-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="c97ca-136">部署 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="c97ca-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="c97ca-137">針對您的叢集，此步驟只需要一次。</span><span class="sxs-lookup"><span data-stu-id="c97ca-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="c97ca-138">使用 [HDInsight 指令碼動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-worker.sh`。</span><span class="sxs-lookup"><span data-stu-id="c97ca-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="c97ca-139">設定</span><span class="sxs-lookup"><span data-stu-id="c97ca-139">Setting</span></span>|<span data-ttu-id="c97ca-140">值</span><span class="sxs-lookup"><span data-stu-id="c97ca-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="c97ca-141">腳本類型</span><span class="sxs-lookup"><span data-stu-id="c97ca-141">Script type</span></span>|<span data-ttu-id="c97ca-142">自訂</span><span class="sxs-lookup"><span data-stu-id="c97ca-142">Custom</span></span>|
|<span data-ttu-id="c97ca-143">名稱</span><span class="sxs-lookup"><span data-stu-id="c97ca-143">Name</span></span>|<span data-ttu-id="c97ca-144">安裝 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="c97ca-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="c97ca-145">Bash 腳本 URI</span><span class="sxs-lookup"><span data-stu-id="c97ca-145">Bash script URI</span></span>|<span data-ttu-id="c97ca-146">您上傳 `install-worker.sh` 的目標 URI。</span><span class="sxs-lookup"><span data-stu-id="c97ca-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="c97ca-147">例如： `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span><span class="sxs-lookup"><span data-stu-id="c97ca-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="c97ca-148">節點類型</span><span class="sxs-lookup"><span data-stu-id="c97ca-148">Node type(s)</span></span>|<span data-ttu-id="c97ca-149">工作</span><span class="sxs-lookup"><span data-stu-id="c97ca-149">Worker</span></span>|
|<span data-ttu-id="c97ca-150">參數</span><span class="sxs-lookup"><span data-stu-id="c97ca-150">Parameters</span></span>|<span data-ttu-id="c97ca-151">`install-worker.sh` 的參數。</span><span class="sxs-lookup"><span data-stu-id="c97ca-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="c97ca-152">例如，若您將 `install-worker.sh` 上傳到 Azure Data Lake Gen 2，它便會是 `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`。</span><span class="sxs-lookup"><span data-stu-id="c97ca-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![指令碼動作影像](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="c97ca-154">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c97ca-154">Run your app</span></span>

<span data-ttu-id="c97ca-155">您可以使用 `spark-submit` 或 Apache Livy 將作業提交到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="c97ca-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="c97ca-156">使用 spark-submit</span><span class="sxs-lookup"><span data-stu-id="c97ca-156">Use spark-submit</span></span>

<span data-ttu-id="c97ca-157">您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="c97ca-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="c97ca-158">`ssh` 到您叢集中的其中一個前端節點。</span><span class="sxs-lookup"><span data-stu-id="c97ca-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="c97ca-159">執行`spark-submit`：</span><span class="sxs-lookup"><span data-stu-id="c97ca-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="c97ca-160">使用 Apache Livy</span><span class="sxs-lookup"><span data-stu-id="c97ca-160">Use Apache Livy</span></span>

<span data-ttu-id="c97ca-161">您可以使用 [Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) 來將適用於 Apache Spark 的 .NET 作業提交到 Azure HDInsight Spark 叢集。</span><span class="sxs-lookup"><span data-stu-id="c97ca-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="c97ca-162">如需詳細資訊，請參閱 [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface) (使用 Apache Livy 的遠端作業)。</span><span class="sxs-lookup"><span data-stu-id="c97ca-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="c97ca-163">您可以使用 `curl`，在 Linux 上執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c97ca-163">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="c97ca-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c97ca-164">Next steps</span></span>

<span data-ttu-id="c97ca-165">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="c97ca-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="c97ca-166">若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。</span><span class="sxs-lookup"><span data-stu-id="c97ca-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c97ca-167">Azure HDInsight 檔</span><span class="sxs-lookup"><span data-stu-id="c97ca-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
