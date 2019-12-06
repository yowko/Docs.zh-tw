---
title: 將適用于 Apache Spark 作業的 .NET 提交至 Databricks
description: 瞭解如何使用 Spark 將 Apache Spark 作業的 .NET 提交至 Databricks-提交和設定 Jar。
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9cd3d40871d4600660957ec268f192ef3e045845
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838348"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="dee34-103">將適用于 Apache Spark 作業的 .NET 提交至 Databricks</span><span class="sxs-lookup"><span data-stu-id="dee34-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="dee34-104">有兩種方式可將 Apache Spark 作業的 .NET 部署至 Databricks： `spark-submit` 並設定 Jar。</span><span class="sxs-lookup"><span data-stu-id="dee34-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span> 

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="dee34-105">使用 spark 部署-提交</span><span class="sxs-lookup"><span data-stu-id="dee34-105">Deploy using spark-submit</span></span>

<span data-ttu-id="dee34-106">您可以使用[spark 提交](https://spark.apache.org/docs/latest/submitting-applications.html)命令，將 Apache Spark 作業的 .net 提交至 Databricks。</span><span class="sxs-lookup"><span data-stu-id="dee34-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="dee34-107">`spark-submit` 只允許提交至隨選建立的叢集。</span><span class="sxs-lookup"><span data-stu-id="dee34-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="dee34-108">流覽至您的 Databricks 工作區，並建立作業。</span><span class="sxs-lookup"><span data-stu-id="dee34-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="dee34-109">選擇您的作業標題，然後選取 [**設定 spark-提交**]。</span><span class="sxs-lookup"><span data-stu-id="dee34-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="dee34-110">在作業設定中貼上下列參數，然後選取 [**確認**]。</span><span class="sxs-lookup"><span data-stu-id="dee34-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="dee34-111">根據您的特定檔案和設定，更新上述參數的內容。</span><span class="sxs-lookup"><span data-stu-id="dee34-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="dee34-112">例如，參考您上傳至 DBFS 的 Microsoft Spark jar 檔案的版本，並使用應用程式的適當名稱和已發佈的應用程式 zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="dee34-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="dee34-113">流覽至您的作業，然後選取 [**編輯**] 來設定作業的叢集。</span><span class="sxs-lookup"><span data-stu-id="dee34-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="dee34-114">根據您想要在部署中使用的 Apache Spark 版本來設定 Databricks Runtime 版本。</span><span class="sxs-lookup"><span data-stu-id="dee34-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="dee34-115">然後選取  **Advanced Options > Init Scripts**，並將 Init Script Path 設定為 `dbfs:/spark-dotnet/db-init.sh`。</span><span class="sxs-lookup"><span data-stu-id="dee34-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="dee34-116">選取 [**確認**] 以確認您的叢集設定。</span><span class="sxs-lookup"><span data-stu-id="dee34-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="dee34-117">流覽至您的作業，然後選取 [**立即執行**]，在新設定的 Spark 叢集上執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="dee34-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="dee34-118">建立作業的叢集需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="dee34-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="dee34-119">建立之後，就會提交您的作業。</span><span class="sxs-lookup"><span data-stu-id="dee34-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="dee34-120">您**可以從 Databricks**工作區的左側功能表中選取 [叢集] 來查看輸出，然後選取 [**驅動程式記錄**]。</span><span class="sxs-lookup"><span data-stu-id="dee34-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="dee34-121">使用 Set Jar 進行部署</span><span class="sxs-lookup"><span data-stu-id="dee34-121">Deploy using Set Jar</span></span>

<span data-ttu-id="dee34-122">或者，您可以在 Databricks 工作區中使用[Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) ，將適用于 Apache Spark 作業的 .net 提交至 Databricks。</span><span class="sxs-lookup"><span data-stu-id="dee34-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="dee34-123">*Set Jar*允許將作業提交至現有的使用中叢集。</span><span class="sxs-lookup"><span data-stu-id="dee34-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="dee34-124">單次設定</span><span class="sxs-lookup"><span data-stu-id="dee34-124">One-time setup</span></span>

1. <span data-ttu-id="dee34-125">流覽至您的 Databricks 叢集，然後從左側功能表中選取 [**作業**]，後面接著 [**設定 JAR**]。</span><span class="sxs-lookup"><span data-stu-id="dee34-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="dee34-126">上傳適當的 `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`。</span><span class="sxs-lookup"><span data-stu-id="dee34-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="dee34-127">修改下列參數，以包含您所發行之可執行檔的正確名稱，以取代 `<your-app-name>`：</span><span class="sxs-lookup"><span data-stu-id="dee34-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="dee34-128">設定叢集，使其指向已設定 init 腳本的現有叢集。</span><span class="sxs-lookup"><span data-stu-id="dee34-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="dee34-129">發佈和執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="dee34-129">Publish and run your app</span></span>

1. <span data-ttu-id="dee34-130">請確定您已發行應用程式，而且您的應用程式程式碼未使用 `SparkSession.Stop()`。</span><span class="sxs-lookup"><span data-stu-id="dee34-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="dee34-131">使用[DATABRICKS CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli)將您的應用程式上傳至 Databricks 叢集。</span><span class="sxs-lookup"><span data-stu-id="dee34-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="dee34-132">例如，使用下列命令，將已發佈的應用程式上傳到您的叢集：</span><span class="sxs-lookup"><span data-stu-id="dee34-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="dee34-133">如果您的應用程式中有任何使用者定義的函式，則必須將應用程式元件（例如包含使用者定義函式的 Dll 及其相依性）放在每個*Microsoft*的工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="dee34-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="dee34-134">將應用程式元件上傳至您的 Databricks 叢集：</span><span class="sxs-lookup"><span data-stu-id="dee34-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="dee34-135">取消批註並修改[db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)中的 [應用程式相依性] 區段，以指向您的應用程式相依性路徑。</span><span class="sxs-lookup"><span data-stu-id="dee34-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="dee34-136">然後，將更新的*db-init.sh*上傳至您的叢集：</span><span class="sxs-lookup"><span data-stu-id="dee34-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="dee34-137">流覽至**Databricks cluster > 作業 > [作業名稱] > 立即執行**以執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="dee34-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dee34-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dee34-138">Next steps</span></span>

* [<span data-ttu-id="dee34-139">開始使用適用於 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="dee34-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="dee34-140">將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="dee34-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="dee34-141">Azure Databricks 文件</span><span class="sxs-lookup"><span data-stu-id="dee34-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
