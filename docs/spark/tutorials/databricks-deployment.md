---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3c9169e2936742c82ba27327ac07f0aa1b4c645c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254048"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="b2082-103">將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="b2082-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="b2082-104">本教學課程會教導如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="b2082-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="b2082-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="b2082-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> - <span data-ttu-id="b2082-106">準備 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="b2082-106">Prepare Microsoft.Spark.Worker</span></span>
> - <span data-ttu-id="b2082-107">發佈您的 Spark .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2082-107">Publish your Spark .NET app</span></span>
> - <span data-ttu-id="b2082-108">將您的應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="b2082-108">Deploy your app to Databricks</span></span>
> - <span data-ttu-id="b2082-109">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="b2082-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2082-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="b2082-110">Prerequisites</span></span>

<span data-ttu-id="b2082-111">開始之前, 請執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="b2082-111">Before you start, do the following:</span></span>

- <span data-ttu-id="b2082-112">下載 [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)。</span><span class="sxs-lookup"><span data-stu-id="b2082-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
- <span data-ttu-id="b2082-113">將 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下載到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b2082-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="b2082-114">這是您稍後用來將適用於 Apache Spark 的 .NET 應用程式相依檔案複製到您 Spark 叢集背景工作節點的協助程式指令碼。</span><span class="sxs-lookup"><span data-stu-id="b2082-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="b2082-115">準備背景工作相依性</span><span class="sxs-lookup"><span data-stu-id="b2082-115">Prepare worker dependencies</span></span>

<span data-ttu-id="b2082-116">**Microsoft.Spark.Worker** 是一種後端元件，存在於您 Spark 叢集的個別背景工作節點上。</span><span class="sxs-lookup"><span data-stu-id="b2082-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="b2082-117">當您想要執行 C# UDF (使用者定義函式) 時，Spark 需要了解如何啟動 .NET CLR 來執行 UDF。</span><span class="sxs-lookup"><span data-stu-id="b2082-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="b2082-118">**Microsoft.Spark.Worker** 會向 Spark 提供類別集合，其會啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="b2082-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="b2082-119">選取要部署在您叢集上的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。</span><span class="sxs-lookup"><span data-stu-id="b2082-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="b2082-120">例如，若您想要使用 `netcoreapp2.1` 的 `.NET for Apache Spark v0.1.0`，您可以下載 [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="b2082-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="b2082-121">將 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上傳到您叢集可以存取的分散式檔案系統 (例如 DBFS)。</span><span class="sxs-lookup"><span data-stu-id="b2082-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="b2082-122">準備適用於 Apache Spark 的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2082-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="b2082-123">遵循[開始使用](get-started.md)教學課程來建置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2082-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="b2082-124">將您的 Spark .NET 應用程式發佈為獨立式應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2082-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="b2082-125">您可以在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b2082-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="b2082-126">為發佈的檔案產生 `<your app>.zip`。</span><span class="sxs-lookup"><span data-stu-id="b2082-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="b2082-127">您可以使用 `zip`，在 Linux 上執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="b2082-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="b2082-128">將下列項目上傳到您叢集可存取的分散式檔案系統 (例如 DBFS)：</span><span class="sxs-lookup"><span data-stu-id="b2082-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   - <span data-ttu-id="b2082-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`：此 jar 已作為 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件的一部分包含在其中，且已共置於您應用程式的建置輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="b2082-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   - `<your app>.zip`
   - <span data-ttu-id="b2082-130">要放在每個執行程式中工作目錄的檔案 (例如相依性檔案或每個背景工作都可存取的通用資料) 或組件 (例如包含您使用者定義函式或您應用程式相依程式庫的 DLL)。</span><span class="sxs-lookup"><span data-stu-id="b2082-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="b2082-131">部署至 Databricks</span><span class="sxs-lookup"><span data-stu-id="b2082-131">Deploy to Databricks</span></span>

<span data-ttu-id="b2082-132">[Databricks](https://databricks.com) 是一種平台，提供使用 Apache Spark 的雲端式巨量資料處理。</span><span class="sxs-lookup"><span data-stu-id="b2082-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="b2082-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) 和 [AWS Databricks](https://databricks.com/aws) 都是以 Linux 為基礎。</span><span class="sxs-lookup"><span data-stu-id="b2082-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="b2082-134">因此，若您想要將應用程式部署到 Databricks，請確認應用程式與 .NET Standard 相容，且您是使用 [.NET Core 編譯器](https://dotnet.microsoft.com/download)來編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2082-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="b2082-135">Databricks 可讓您將適用於 Apache Spark 的 .NET 應用程式部署到現有使用中叢集，或在您每次啟動作業時建立新的叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="b2082-136">這需要在您提交適用於 Apache Spark 的 .NET 應用程式前，先安裝 **Microsoft.Spark.Worker**。</span><span class="sxs-lookup"><span data-stu-id="b2082-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="b2082-137">部署 Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="b2082-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="b2082-138">針對叢集，此步驟只需要一次。</span><span class="sxs-lookup"><span data-stu-id="b2082-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="b2082-139">下載 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) 到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b2082-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="b2082-140">修改 **db-init.sh** 以指向您要下載和在您叢集上安裝的 **Microsoft.Spark.Worker** 版本。</span><span class="sxs-lookup"><span data-stu-id="b2082-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="b2082-141">安裝 [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)。</span><span class="sxs-lookup"><span data-stu-id="b2082-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="b2082-142">Databricks CLI 的[設定驗證](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication)詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b2082-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="b2082-143">使用下列命令將檔案上傳到您的 Databricks 叢集：</span><span class="sxs-lookup"><span data-stu-id="b2082-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="b2082-144">移至您的 Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="b2082-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="b2082-145">從左側功能表中選取 [Clusters] \(叢集\)，然後選取 [Create Cluster] \(建立叢集\)。</span><span class="sxs-lookup"><span data-stu-id="b2082-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="b2082-146">適當地設定叢集後，請設定**初始指令碼**並建立叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![指令碼動作影像](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="b2082-148">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="b2082-148">Run your app</span></span> 

<span data-ttu-id="b2082-149">您可以使用 `set JAR` 或 `spark-submit` 來將您的作業提交到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="b2082-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="b2082-150">使用 Set JAR</span><span class="sxs-lookup"><span data-stu-id="b2082-150">Use Set JAR</span></span>

<span data-ttu-id="b2082-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) 可讓您將作業提交到現有使用中叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="b2082-152">一次性設定</span><span class="sxs-lookup"><span data-stu-id="b2082-152">One-time setup</span></span>

1. <span data-ttu-id="b2082-153">前往您的 Databricks 叢集，並從左側功能表中選取 [Jobs] \(作業\)。</span><span class="sxs-lookup"><span data-stu-id="b2082-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="b2082-154">然後選取 [Set JAR]。</span><span class="sxs-lookup"><span data-stu-id="b2082-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="b2082-155">上傳適當的 `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` 檔案。</span><span class="sxs-lookup"><span data-stu-id="b2082-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="b2082-156">適當地設定參數。</span><span class="sxs-lookup"><span data-stu-id="b2082-156">Set the parameters appropriately.</span></span>

   ```
   Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. <span data-ttu-id="b2082-157">設定 [Cluster] \(叢集\) 以指向您在前一節中為其建立**初始指令碼**的現有叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-157">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="b2082-158">發佈和執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="b2082-158">Publish and run your app</span></span>

1. <span data-ttu-id="b2082-159">使用 [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) 來將應用程式上傳到您的 Databricks 叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-159">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="b2082-160">此步驟只有在應用程式組件 (例如包含使用者定義函式及其相依性的 DLL) 需要放置在每個 **Microsoft.Spark.Worker** 的工作目錄時才需要。</span><span class="sxs-lookup"><span data-stu-id="b2082-160">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="b2082-161">將應用程式組件上傳到您的 Databricks 叢集</span><span class="sxs-lookup"><span data-stu-id="b2082-161">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="b2082-162">取消註解並修改 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 中的應用程式相依性區段，以指向應用程式相依性路徑並上傳到您的 Databricks 叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-162">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="b2082-163">重新啟動您的叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-163">Restart your cluster.</span></span>

3. <span data-ttu-id="b2082-164">前往您位於 Databricks 工作區中的 Databricks 叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-164">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="b2082-165">在 [Jobs] \(作業\) 下方，選取作業，然後選取 [Run Now] \(立即執行\) 來執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="b2082-165">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="b2082-166">使用 spark-submit</span><span class="sxs-lookup"><span data-stu-id="b2082-166">Use spark-submit</span></span>

<span data-ttu-id="b2082-167">[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令可讓您將作業提交到新的叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-167">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="b2082-168">[建立作業](https://docs.databricks.com/user-guide/jobs.html)並選取 [Configure spark-submit] \(設定 spark-submit\)。</span><span class="sxs-lookup"><span data-stu-id="b2082-168">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="b2082-169">搭配下列參數設定 `spark-submit`：</span><span class="sxs-lookup"><span data-stu-id="b2082-169">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="b2082-170">前往您位於 Databricks 工作區中的 Databricks 叢集。</span><span class="sxs-lookup"><span data-stu-id="b2082-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="b2082-171">在 [Jobs] \(作業\) 下方，選取作業，然後選取 [Run Now] \(立即執行\) 來執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="b2082-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2082-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b2082-172">Next steps</span></span>

<span data-ttu-id="b2082-173">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="b2082-173">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="b2082-174">若要深入了解 Databricks，請繼續前往 Azure Databricks 文件。</span><span class="sxs-lookup"><span data-stu-id="b2082-174">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2082-175">Azure Databricks 文件</span><span class="sxs-lookup"><span data-stu-id="b2082-175">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
