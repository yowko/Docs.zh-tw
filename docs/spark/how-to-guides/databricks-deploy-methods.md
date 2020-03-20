---
title: 將阿帕奇火花作業的 .NET 提交到資料磚塊
description: 瞭解如何使用火花提交和設置 Jar 將 Apache Spark 的 .NET 作業提交到 Databricks。
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187614"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="3d1d8-103">將阿帕奇火花作業的 .NET 提交到資料磚塊</span><span class="sxs-lookup"><span data-stu-id="3d1d8-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="3d1d8-104">有兩種方法可以將的 .NET 用於 Apache Spark 作業部署到`spark-submit`資料磚塊：和"設置 Jar"。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="3d1d8-105">使用火花提交進行部署</span><span class="sxs-lookup"><span data-stu-id="3d1d8-105">Deploy using spark-submit</span></span>

<span data-ttu-id="3d1d8-106">您可以使用[火花提交](https://spark.apache.org/docs/latest/submitting-applications.html)命令將 Apache Spark 作業的 .NET 提交到資料磚塊。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="3d1d8-107">`spark-submit`只允許提交到按需創建的群集。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="3d1d8-108">導航到資料磚塊工作區並創建作業。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="3d1d8-109">為作業選擇標題，然後選擇 **"配置火花提交**"。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="3d1d8-110">在作業配置中粘貼以下參數，然後選擇 **"確認**"。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="3d1d8-111">根據您的特定檔和配置更新上述參數的內容。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="3d1d8-112">例如，引用您上傳到 DBFS 的 Microsoft.Spark jar 檔的版本，並使用應用和已發佈的應用 ZIP 檔案的適當名稱。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="3d1d8-113">導航到作業並選擇 **"編輯"** 以配置作業的群集。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="3d1d8-114">根據要在部署中使用 Apache Spark 的版本設置資料磚塊執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="3d1d8-115">然後選擇 **"以來"腳本>的高級選項**，並將 Init`dbfs:/spark-dotnet/db-init.sh`腳本路徑設置為 。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="3d1d8-116">選擇 **"確認**"以確認群集設置。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="3d1d8-117">導航到作業，然後選擇 **"立即運行"** 以在新配置的 Spark 群集上運行作業。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="3d1d8-118">創建作業的群集需要幾分鐘時間。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="3d1d8-119">創建作業後，將提交作業。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="3d1d8-120">您可以通過從資料磚塊工作區的左側功能表中選擇 **"群集"** 來查看輸出，然後選擇**驅動程式日誌**。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="3d1d8-121">使用"設置 Jar"進行部署</span><span class="sxs-lookup"><span data-stu-id="3d1d8-121">Deploy using Set Jar</span></span>

<span data-ttu-id="3d1d8-122">或者，您可以使用資料磚塊工作區中的["設置 Jar"](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job)將 Apache Spark 作業的 .NET 提交到資料磚塊。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="3d1d8-123">*Set Jar*允許作業提交到現有活動群集。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="3d1d8-124">單次設定</span><span class="sxs-lookup"><span data-stu-id="3d1d8-124">One-time setup</span></span>

1. <span data-ttu-id="3d1d8-125">導航到資料磚塊群集，並從左側功能表中選擇 **"作業"，** 然後**選擇"設置 JAR**"。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="3d1d8-126">上傳相應的`microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="3d1d8-127">修改以下參數以包括您以： 代替發佈的可執行檔的正確名稱`<your-app-name>`：</span><span class="sxs-lookup"><span data-stu-id="3d1d8-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="3d1d8-128">將群集配置為指向已為其設置 init 腳本的現有群集。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="3d1d8-129">發佈和執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="3d1d8-129">Publish and run your app</span></span>

1. <span data-ttu-id="3d1d8-130">確保已發佈應用，並且應用程式代碼不使用`SparkSession.Stop()`。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="3d1d8-131">使用[資料塊 CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli)將應用程式上載到資料磚群集。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="3d1d8-132">例如，使用以下命令將已發佈的應用上載到群集：</span><span class="sxs-lookup"><span data-stu-id="3d1d8-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="3d1d8-133">如果應用中有任何使用者定義的函數，則需要將應用程式集（如包含使用者定義的函數及其依賴項的 DLL）放置在每個*Microsoft.Spark.Worker*的工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="3d1d8-134">將應用程式程式集上載到 Databricks 群集：</span><span class="sxs-lookup"><span data-stu-id="3d1d8-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="3d1d8-135">db-init.sh取消注釋並修改應用依賴項[部分，以](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)指向應用依賴項路徑。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="3d1d8-136">然後，將更新*db-init.sh*上載到群集：</span><span class="sxs-lookup"><span data-stu-id="3d1d8-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="3d1d8-137">導航到**資料磚塊群集>作業> [作業名稱] >立即運行**以運行作業。</span><span class="sxs-lookup"><span data-stu-id="3d1d8-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3d1d8-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3d1d8-138">Next steps</span></span>

* [<span data-ttu-id="3d1d8-139">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3d1d8-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="3d1d8-140">將 .NET for Apache Spark 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="3d1d8-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="3d1d8-141">Azure Databricks 文件</span><span class="sxs-lookup"><span data-stu-id="3d1d8-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
