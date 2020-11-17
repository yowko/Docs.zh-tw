---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: dd1cfdf12266b55d9dbc0210479b89ba68c59a38
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688068"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="f0857-103">將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f0857-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="f0857-104">本教學課程會教導如何將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="f0857-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="f0857-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) 是一種受控叢集平台，其簡化在 AWS 上執行巨量資料架構。</span><span class="sxs-lookup"><span data-stu-id="f0857-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

<span data-ttu-id="f0857-106">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="f0857-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f0857-107">準備 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="f0857-107">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="f0857-108">發佈您的 Spark .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="f0857-108">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="f0857-109">將您的應用程式部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f0857-109">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="f0857-110">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="f0857-110">Run your app</span></span>

> [!Note]
> <span data-ttu-id="f0857-111">以 Linux 為基礎的 AWS EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="f0857-111">AWS EMR Spark is Linux-based.</span></span> <span data-ttu-id="f0857-112">因此，如果您想要將應用程式部署至 AWS EMR Spark，請確定您的應用程式 .NET Standard 相容，且您使用 .NET Core 編譯器來編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0857-112">Therefore, if you are interested in deploying your app to AWS EMR Spark, make sure your app is .NET Standard compatible and that you use .NET Core compiler to compile your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0857-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f0857-113">Prerequisites</span></span>

<span data-ttu-id="f0857-114">開始之前，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f0857-114">Before you start, do the following:</span></span>

* <span data-ttu-id="f0857-115">下載 [AWS CLI](https://aws.amazon.com/cli/)。</span><span class="sxs-lookup"><span data-stu-id="f0857-115">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="f0857-116">將 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下載到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="f0857-116">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="f0857-117">這是您稍後用來將適用於 Apache Spark 的 .NET 應用程式相依檔案複製到您 Spark 叢集背景工作節點的協助程式指令碼。</span><span class="sxs-lookup"><span data-stu-id="f0857-117">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="f0857-118">準備背景工作相依性</span><span class="sxs-lookup"><span data-stu-id="f0857-118">Prepare worker dependencies</span></span>

<span data-ttu-id="f0857-119">**在您** spark 叢集的個別背景工作節點上，則為後端元件。</span><span class="sxs-lookup"><span data-stu-id="f0857-119">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="f0857-120">當您想要 (使用者定義函數) 執行 c # UDF 時，Spark 需要瞭解如何啟動 .NET CLR 以執行 UDF。</span><span class="sxs-lookup"><span data-stu-id="f0857-120">When you want to execute a C# UDF (User-Defined Function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="f0857-121">**Microsoft.Spark.Worker** 會向 Spark 提供類別集合，其會啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="f0857-121">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="f0857-122">選取要部署在您叢集上的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。</span><span class="sxs-lookup"><span data-stu-id="f0857-122">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="f0857-123">例如，如果您想要 `.NET for Apache Spark v1.0.0` 使用 `netcoreapp3.1` ，您可以下載 [netcoreapp 3.1. linux-x64-1.0.0. gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="f0857-123">For example, if you want `.NET for Apache Spark v1.0.0` using `netcoreapp3.1`, you'd download [Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span>

2. <span data-ttu-id="f0857-124">將 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上傳到您叢集可以存取的分散式檔案系統 (例如 S3)。</span><span class="sxs-lookup"><span data-stu-id="f0857-124">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="f0857-125">準備適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="f0857-125">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="f0857-126">遵循[開始使用](get-started.md)教學課程來建置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0857-126">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="f0857-127">將您的 Spark .NET 應用程式發佈為獨立式應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0857-127">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="f0857-128">在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="f0857-128">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="f0857-129">為發佈的檔案產生 `<your app>.zip`。</span><span class="sxs-lookup"><span data-stu-id="f0857-129">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="f0857-130">使用 `zip` 在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="f0857-130">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="f0857-131">將下列項目上傳到您叢集可存取的分散式檔案系統 (例如 S3)：</span><span class="sxs-lookup"><span data-stu-id="f0857-131">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="f0857-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`：此 jar 隨附于 [Microsoft Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件中，並在應用程式的組建輸出目錄中共置。</span><span class="sxs-lookup"><span data-stu-id="f0857-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="f0857-133">要放在每個執行程式中工作目錄的檔案 (例如相依性檔案或每個背景工作都可存取的通用資料) 或組件 (例如包含您使用者定義函式或您應用程式相依程式庫的 DLL)。</span><span class="sxs-lookup"><span data-stu-id="f0857-133">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="f0857-134">部署至 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="f0857-134">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="f0857-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) 是一種受控叢集平台，其簡化在 AWS 上執行巨量資料架構。</span><span class="sxs-lookup"><span data-stu-id="f0857-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="f0857-136">Amazon EMR Spark 是以 Linux 為基礎。</span><span class="sxs-lookup"><span data-stu-id="f0857-136">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="f0857-137">因此，若您想要將應用程式部署到 Amazon EMR Spark，請確認應用程式與 .NET Standard 相容，且您是使用 [.NET Core 編譯器](https://dotnet.microsoft.com/download)來編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0857-137">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="f0857-138">部署 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="f0857-138">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="f0857-139">僅在建立叢集時才需要此步驟。</span><span class="sxs-lookup"><span data-stu-id="f0857-139">This step is only required at cluster creation.</span></span>

<span data-ttu-id="f0857-140">使用[啟動程序動作](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)在叢集建立期間執行 `install-worker.sh`。</span><span class="sxs-lookup"><span data-stu-id="f0857-140">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="f0857-141">使用 AWS CLI 在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="f0857-141">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="f0857-142">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="f0857-142">Run your app</span></span>

<span data-ttu-id="f0857-143">有兩種方式可以在 Amazon EMR Spark 上執行您的應用程式：spark-submit 和 Amazon EMR 步驟。</span><span class="sxs-lookup"><span data-stu-id="f0857-143">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="f0857-144">使用 spark-submit</span><span class="sxs-lookup"><span data-stu-id="f0857-144">Use spark-submit</span></span>

<span data-ttu-id="f0857-145">您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Amazon EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="f0857-145">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="f0857-146">`ssh` 到叢集中的其中一個節點。</span><span class="sxs-lookup"><span data-stu-id="f0857-146">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="f0857-147">執行 `spark-submit`。</span><span class="sxs-lookup"><span data-stu-id="f0857-147">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="f0857-148">使用 Amazon EMR 步驟</span><span class="sxs-lookup"><span data-stu-id="f0857-148">Use Amazon EMR Steps</span></span>

<span data-ttu-id="f0857-149">[Amazon EMR 步驟](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html)可以用來將作業提交到 EMR 叢集上安裝的 Spark 架構。</span><span class="sxs-lookup"><span data-stu-id="f0857-149">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="f0857-150">使用 AWS CLI 在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="f0857-150">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="f0857-151">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f0857-151">Next steps</span></span>

<span data-ttu-id="f0857-152">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark。</span><span class="sxs-lookup"><span data-stu-id="f0857-152">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="f0857-153">如需適用於 Apache Spark 的 .NET 範例專案，請繼續前往 GitHub。</span><span class="sxs-lookup"><span data-stu-id="f0857-153">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f0857-154">適用於 Apache Spark 的 .NET 範例</span><span class="sxs-lookup"><span data-stu-id="f0857-154">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
