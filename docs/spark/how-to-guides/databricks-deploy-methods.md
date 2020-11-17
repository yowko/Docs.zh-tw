---
title: 將 Apache Spark 作業的 .NET 提交至 Databricks
description: 瞭解如何將 Apache Spark 作業的 .NET 提交至使用 Spark 提交和設定 Jar 的 Databricks。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4d37383ccb3c9b311e0fbd0ada195ac20113e505
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688198"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="4a71b-103">將 Apache Spark 作業的 .NET 提交至 Databricks</span><span class="sxs-lookup"><span data-stu-id="4a71b-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="4a71b-104">您可以在 Databricks 叢集上執行您的 .NET 以進行 Apache Spark 作業，但它並不是現成可用。</span><span class="sxs-lookup"><span data-stu-id="4a71b-104">You can run your .NET for Apache Spark jobs on Databricks clusters, but it is not available out-of-the-box.</span></span> <span data-ttu-id="4a71b-105">有兩種方式可將 Apache Spark 作業的 .NET 部署至 Databricks： `spark-submit` 和設定 Jar。</span><span class="sxs-lookup"><span data-stu-id="4a71b-105">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="4a71b-106">使用 spark 部署-提交</span><span class="sxs-lookup"><span data-stu-id="4a71b-106">Deploy using spark-submit</span></span>

<span data-ttu-id="4a71b-107">您可以使用 [spark 提交](https://spark.apache.org/docs/latest/submitting-applications.html) 命令，將 Apache Spark 作業的 .net 提交至 Databricks。</span><span class="sxs-lookup"><span data-stu-id="4a71b-107">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="4a71b-108">`spark-submit` 只允許提交至隨選建立的叢集。</span><span class="sxs-lookup"><span data-stu-id="4a71b-108">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="4a71b-109">流覽至您的 Databricks 工作區，並建立作業。</span><span class="sxs-lookup"><span data-stu-id="4a71b-109">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="4a71b-110">選擇您作業的標題，然後選取 [ **設定 spark-提交**]。</span><span class="sxs-lookup"><span data-stu-id="4a71b-110">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="4a71b-111">在作業設定中貼上下列參數，然後選取 [ **確認**]。</span><span class="sxs-lookup"><span data-stu-id="4a71b-111">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="4a71b-112">根據您的特定檔案和設定，更新上述參數的內容。</span><span class="sxs-lookup"><span data-stu-id="4a71b-112">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="4a71b-113">例如，參考您上傳至 DBFS 的 Microsoft .jar jar 檔案版本，並使用應用程式的適當名稱和已發佈的應用程式 zip 檔。</span><span class="sxs-lookup"><span data-stu-id="4a71b-113">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="4a71b-114">流覽至您的作業，然後選取 [ **編輯** ] 以設定作業的叢集。</span><span class="sxs-lookup"><span data-stu-id="4a71b-114">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="4a71b-115">根據您想要在部署中使用的 Apache Spark 版本，設定 Databricks Runtime 版本。</span><span class="sxs-lookup"><span data-stu-id="4a71b-115">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="4a71b-116">然後選取 [ **Advanced Options > Init** Script]，並將 Init Script Path 設定為 `dbfs:/spark-dotnet/db-init.sh` 。</span><span class="sxs-lookup"><span data-stu-id="4a71b-116">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="4a71b-117">選取 [ **確認** ] 以確認您的叢集設定。</span><span class="sxs-lookup"><span data-stu-id="4a71b-117">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="4a71b-118">流覽至您的作業，然後選取 [ **立即執行** ]，在新設定的 Spark 叢集上執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="4a71b-118">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="4a71b-119">建立作業的叢集需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="4a71b-119">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="4a71b-120">一旦建立之後，您的作業就會提交。</span><span class="sxs-lookup"><span data-stu-id="4a71b-120">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="4a71b-121">您 **可以從 Databricks** 工作區的左側功能表中選取 [叢集] 來查看輸出，然後選取 [ **驅動程式記錄** 檔]。</span><span class="sxs-lookup"><span data-stu-id="4a71b-121">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="4a71b-122">使用 Set Jar 進行部署</span><span class="sxs-lookup"><span data-stu-id="4a71b-122">Deploy using Set Jar</span></span>

<span data-ttu-id="4a71b-123">或者，您可以在 Databricks 工作區中使用 [Set Jar](/azure/databricks/jobs#--create-a-job) ，將適用于 Apache Spark 作業的 .net 提交給 Databricks。</span><span class="sxs-lookup"><span data-stu-id="4a71b-123">Alternatively, you can use [Set Jar](/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="4a71b-124">*Set Jar* 允許將工作提交至現有的使用中叢集。</span><span class="sxs-lookup"><span data-stu-id="4a71b-124">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="4a71b-125">單次設定</span><span class="sxs-lookup"><span data-stu-id="4a71b-125">One-time setup</span></span>

1. <span data-ttu-id="4a71b-126">流覽至您的 Databricks 叢集，然後從左側功能表中選取 [ **作業** ]，接著 **設定 [JAR**]。</span><span class="sxs-lookup"><span data-stu-id="4a71b-126">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="4a71b-127">上傳適當的 `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` 。</span><span class="sxs-lookup"><span data-stu-id="4a71b-127">Upload the appropriate `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`.</span></span>

3. <span data-ttu-id="4a71b-128">修改下列參數，以包含您所發行之可執行檔的正確名稱，以取代 `<your-app-name>` ：</span><span class="sxs-lookup"><span data-stu-id="4a71b-128">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="4a71b-129">設定叢集以指向您已設定 init 腳本的現有叢集。</span><span class="sxs-lookup"><span data-stu-id="4a71b-129">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="4a71b-130">發佈和執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="4a71b-130">Publish and run your app</span></span>

1. <span data-ttu-id="4a71b-131">確定您已發佈您的應用程式，且您的應用程式程式碼未使用 `SparkSession.Stop()` 。</span><span class="sxs-lookup"><span data-stu-id="4a71b-131">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="4a71b-132">使用 [DATABRICKS CLI](/azure/databricks/dev-tools/databricks-cli) 將應用程式上傳至您的 Databricks 叢集。</span><span class="sxs-lookup"><span data-stu-id="4a71b-132">Use [Databricks CLI](/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="4a71b-133">例如，使用下列命令，將已發佈的應用程式上傳至您的叢集：</span><span class="sxs-lookup"><span data-stu-id="4a71b-133">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="4a71b-134">如果您的應用程式中有任何使用者定義函數，則應用程式元件（例如包含使用者定義函式的 Dll 以及其相依性）必須放 *在每個* app.config 的工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="4a71b-134">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="4a71b-135">將您的應用程式元件上傳至 Databricks 叢集：</span><span class="sxs-lookup"><span data-stu-id="4a71b-135">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="4a71b-136">取消批註並修改 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 中的應用程式相依性區段，以指向您的應用程式相依性路徑。</span><span class="sxs-lookup"><span data-stu-id="4a71b-136">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="4a71b-137">然後，將更新的 *db-init.sh* 上傳至您的叢集：</span><span class="sxs-lookup"><span data-stu-id="4a71b-137">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="4a71b-138">流覽至 **Databricks 叢集 > 作業 > [作業名稱] > 立即執行** 以執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="4a71b-138">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a71b-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4a71b-139">Next steps</span></span>

* [<span data-ttu-id="4a71b-140">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="4a71b-140">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="4a71b-141">將 .NET for Apache Spark 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="4a71b-141">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="4a71b-142">Azure Databricks 文件</span><span class="sxs-lookup"><span data-stu-id="4a71b-142">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
