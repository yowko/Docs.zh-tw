---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 HDInsight。
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e6b2fdd1818250c47ce6cb64439ecab58ae99ad8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617635"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="a3120-103">教學課程：將適用于 Apache Spark 應用程式的 .NET 部署至 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a3120-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="a3120-104">本教學課程會教您如何透過 Azure HDInsight 叢集，將 Apache Spark 應用程式的 .NET 部署至雲端。</span><span class="sxs-lookup"><span data-stu-id="a3120-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="a3120-105">HDInsight 可讓您更輕鬆地在 Azure 中建立和設定 Spark 叢集，因為 HDInsight 中的 Spark 叢集與 Azure 儲存體和 Azure Data Lake Storage 相容。</span><span class="sxs-lookup"><span data-stu-id="a3120-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="a3120-106">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="a3120-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a3120-107">使用 Azure 儲存體總管存取儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="a3120-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="a3120-108">建立 Azure HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="a3120-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="a3120-109">發行您的 .NET for Apache Spark 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3120-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="a3120-110">建立並執行 HDInsight 腳本動作。</span><span class="sxs-lookup"><span data-stu-id="a3120-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="a3120-111">在 HDInsight 叢集上執行適用于 Apache Spark 應用程式的 .NET。</span><span class="sxs-lookup"><span data-stu-id="a3120-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="a3120-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="a3120-112">Prerequisites</span></span>

<span data-ttu-id="a3120-113">開始之前，請執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="a3120-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="a3120-114">如果您沒有 Azure 訂用帳戶，請建立[免費帳戶](https://azure.microsoft.com/free/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="a3120-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="a3120-115">登入 [Azure 入口網站](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="a3120-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="a3120-116">在您的[Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)、 [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)或[MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)電腦上安裝 Azure 儲存體總管。</span><span class="sxs-lookup"><span data-stu-id="a3120-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="a3120-117">完成[Apache Spark 的 .net-在10分鐘內開始](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)使用教學課程。</span><span class="sxs-lookup"><span data-stu-id="a3120-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="a3120-118">存取您的儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="a3120-118">Access your storage accounts</span></span>

1. <span data-ttu-id="a3120-119">開啟 [Azure 儲存體總管]。</span><span class="sxs-lookup"><span data-stu-id="a3120-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="a3120-120">選取左側功能表上的 [**新增帳戶**]，然後登入您的 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a3120-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![從儲存體總管登入 Azure 帳戶](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="a3120-122">登入之後，您應該會看到您擁有的所有儲存體帳戶，以及已上傳至儲存體帳戶的任何資源。</span><span class="sxs-lookup"><span data-stu-id="a3120-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="a3120-123">建立 HDInsight 叢集</span><span class="sxs-lookup"><span data-stu-id="a3120-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3120-124">HDInsight 叢集的計費是以每分鐘為單位，即使您不使用它們也一樣。</span><span class="sxs-lookup"><span data-stu-id="a3120-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="a3120-125">請務必在使用完叢集後將其刪除。</span><span class="sxs-lookup"><span data-stu-id="a3120-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="a3120-126">如需詳細資訊，請參閱本教學課程的[清理資源](#clean-up-resources)一節。</span><span class="sxs-lookup"><span data-stu-id="a3120-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="a3120-127">請造訪[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="a3120-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="a3120-128">選取 [+ 建立資源]。</span><span class="sxs-lookup"><span data-stu-id="a3120-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="a3120-129">然後，從 [**分析**] 類別中選取 [ **HDInsight** ]。</span><span class="sxs-lookup"><span data-stu-id="a3120-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![從 Azure 入口網站建立 HDInsight 資源](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="a3120-131">在 [基本]\*\*\*\* 下方，提供下列值：</span><span class="sxs-lookup"><span data-stu-id="a3120-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="a3120-132">屬性</span><span class="sxs-lookup"><span data-stu-id="a3120-132">Property</span></span>  |<span data-ttu-id="a3120-133">描述</span><span class="sxs-lookup"><span data-stu-id="a3120-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="a3120-134">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="a3120-134">Subscription</span></span>  | <span data-ttu-id="a3120-135">從下拉式選單中，選擇其中一個作用中的 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="a3120-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="a3120-136">資源群組</span><span class="sxs-lookup"><span data-stu-id="a3120-136">Resource group</span></span> | <span data-ttu-id="a3120-137">指定您是要建立新的資源群組，還是使用現有資源群組。</span><span class="sxs-lookup"><span data-stu-id="a3120-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="a3120-138">資源群組是存放 Azure 方案相關資源的容器。</span><span class="sxs-lookup"><span data-stu-id="a3120-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="a3120-139">叢集名稱</span><span class="sxs-lookup"><span data-stu-id="a3120-139">Cluster name</span></span> | <span data-ttu-id="a3120-140">提供 HDInsight Spark 叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3120-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="a3120-141">Location</span><span class="sxs-lookup"><span data-stu-id="a3120-141">Location</span></span>   | <span data-ttu-id="a3120-142">選取資源群組的位置。</span><span class="sxs-lookup"><span data-stu-id="a3120-142">Select a location for the resource group.</span></span> <span data-ttu-id="a3120-143">此範本會使用這個位置，用於建立叢集以及預設叢集儲存體。</span><span class="sxs-lookup"><span data-stu-id="a3120-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="a3120-144">叢集類型</span><span class="sxs-lookup"><span data-stu-id="a3120-144">Cluster type</span></span>| <span data-ttu-id="a3120-145">選取 [spark]\*\*\*\* 作為叢集類型。</span><span class="sxs-lookup"><span data-stu-id="a3120-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="a3120-146">叢集版本</span><span class="sxs-lookup"><span data-stu-id="a3120-146">Cluster version</span></span>|<span data-ttu-id="a3120-147">一旦選取叢集類型，此欄位將會以預設版本自動填入。</span><span class="sxs-lookup"><span data-stu-id="a3120-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="a3120-148">選取 [2.3] 或 [2.4] 版本的 Spark。</span><span class="sxs-lookup"><span data-stu-id="a3120-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="a3120-149">叢集登入使用者名稱</span><span class="sxs-lookup"><span data-stu-id="a3120-149">Cluster login username</span></span>| <span data-ttu-id="a3120-150">輸入叢集登入使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a3120-150">Enter the cluster login username.</span></span>  <span data-ttu-id="a3120-151">預設名稱為 *admin*。</span><span class="sxs-lookup"><span data-stu-id="a3120-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="a3120-152">叢集登入密碼</span><span class="sxs-lookup"><span data-stu-id="a3120-152">Cluster login password</span></span>| <span data-ttu-id="a3120-153">輸入任何登入密碼。</span><span class="sxs-lookup"><span data-stu-id="a3120-153">Enter any login password.</span></span> |
    |<span data-ttu-id="a3120-154">安全殼層 (SSH) 使用者名稱</span><span class="sxs-lookup"><span data-stu-id="a3120-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="a3120-155">輸入 SSH 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a3120-155">Enter the SSH username.</span></span> <span data-ttu-id="a3120-156">根據預設，此帳戶會共用與「叢集登入使用者名稱」  帳戶相同的密碼。</span><span class="sxs-lookup"><span data-stu-id="a3120-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="a3120-157">完成時，選取 [下一步:  儲存體>>] 繼續前往 [儲存體]  頁面。</span><span class="sxs-lookup"><span data-stu-id="a3120-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="a3120-158">在 [儲存體]  下方，提供下列值：</span><span class="sxs-lookup"><span data-stu-id="a3120-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="a3120-159">屬性</span><span class="sxs-lookup"><span data-stu-id="a3120-159">Property</span></span>  |<span data-ttu-id="a3120-160">描述</span><span class="sxs-lookup"><span data-stu-id="a3120-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="a3120-161">主要儲存體類型</span><span class="sxs-lookup"><span data-stu-id="a3120-161">Primary storage type</span></span>|<span data-ttu-id="a3120-162">使用預設值 [Azure 儲存體]  。</span><span class="sxs-lookup"><span data-stu-id="a3120-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="a3120-163">選取方法</span><span class="sxs-lookup"><span data-stu-id="a3120-163">Selection method</span></span>|<span data-ttu-id="a3120-164">使用預設值 [從清單中選取]  。</span><span class="sxs-lookup"><span data-stu-id="a3120-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="a3120-165">主要儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="a3120-165">Primary storage account</span></span>|<span data-ttu-id="a3120-166">選擇您的訂用帳戶，以及該訂用帳戶內的其中一個作用中儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="a3120-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="a3120-167">容器</span><span class="sxs-lookup"><span data-stu-id="a3120-167">Container</span></span>|<span data-ttu-id="a3120-168">此容器是儲存體帳戶中的特定 blob 容器，您的叢集會在此尋找檔案以在雲端中執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3120-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="a3120-169">您可以為它提供任何可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3120-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="a3120-170">在 [檢閱 + 建立]  底下，選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="a3120-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="a3120-171">大約需要 20 分鐘的時間來建立叢集。</span><span class="sxs-lookup"><span data-stu-id="a3120-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="a3120-172">您必須先建立叢集，才能繼續進行下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a3120-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="a3120-173">發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a3120-173">Publish your app</span></span>

<span data-ttu-id="a3120-174">接下來，您會發佈在 .Net 中建立[Apache Spark-開始使用10分鐘](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教學課程的*mySparkApp* ，這可讓您的 Spark 叢集存取執行應用程式所需的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="a3120-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="a3120-175">執行下列命令以發佈*mySparkApp*：</span><span class="sxs-lookup"><span data-stu-id="a3120-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="a3120-176">**在 Windows 上：**</span><span class="sxs-lookup"><span data-stu-id="a3120-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="a3120-177">**在 Linux 上：**</span><span class="sxs-lookup"><span data-stu-id="a3120-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="a3120-178">請執行下列工作來壓縮已發佈的應用程式檔，讓您可以輕鬆地將它們上傳到您的 HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="a3120-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="a3120-179">**在 Windows 上：**</span><span class="sxs-lookup"><span data-stu-id="a3120-179">**On Windows:**</span></span>

   <span data-ttu-id="a3120-180">流覽至*mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64*。</span><span class="sxs-lookup"><span data-stu-id="a3120-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="a3120-181">然後，在 [**發行**資料夾] 上按一下滑鼠右鍵，然後選取 **[傳送至 > 壓縮的（zipped）資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="a3120-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="a3120-182">將新資料夾命名為**publish.zip**。</span><span class="sxs-lookup"><span data-stu-id="a3120-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="a3120-183">**在 Linux 上，執行下列命令：**</span><span class="sxs-lookup"><span data-stu-id="a3120-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="a3120-184">將檔案上傳至 Azure</span><span class="sxs-lookup"><span data-stu-id="a3120-184">Upload files to Azure</span></span>

<span data-ttu-id="a3120-185">接下來，您可以使用 Azure 儲存體總管，將下列五個檔案上傳至您為叢集儲存體選擇的 blob 容器：</span><span class="sxs-lookup"><span data-stu-id="a3120-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="a3120-186">Microsoft. Spark. 背景工作角色</span><span class="sxs-lookup"><span data-stu-id="a3120-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="a3120-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="a3120-187">install-worker.sh</span></span>
* <span data-ttu-id="a3120-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="a3120-188">publish.zip</span></span>
* <span data-ttu-id="a3120-189">microsoft-spark-2.3. x-0.3.0 .jar</span><span class="sxs-lookup"><span data-stu-id="a3120-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="a3120-190">input.txt。</span><span class="sxs-lookup"><span data-stu-id="a3120-190">input.txt.</span></span>

1. <span data-ttu-id="a3120-191">開啟 Azure 儲存體總管，然後從左側功能表流覽至您的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="a3120-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="a3120-192">向下切入至儲存體帳戶中**Blob 容器**下的叢集 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="a3120-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="a3120-193">Apache Spark*可協助執行*您的應用程式，例如您可能已撰寫的任何使用者定義函數（udf）。</span><span class="sxs-lookup"><span data-stu-id="a3120-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="a3120-194">下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="a3120-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="a3120-195">然後，選取 [**上傳**] Azure 儲存體總管中傳背景工作角色。</span><span class="sxs-lookup"><span data-stu-id="a3120-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![將檔案上傳至 Azure 儲存體總管](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="a3120-197">*Install-worker.sh*是一個腳本，可讓您將 Apache Spark 相依檔案的 .net 複製到叢集的節點中。</span><span class="sxs-lookup"><span data-stu-id="a3120-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="a3120-198">在您的本機電腦上建立名為**install-worker.sh**的新檔案，並貼上位於 GitHub 的[install-worker.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。</span><span class="sxs-lookup"><span data-stu-id="a3120-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="a3120-199">然後，將*install-worker.sh*上傳至您的 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="a3120-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="a3120-200">您的叢集需要包含應用程式已發佈檔案的 publish.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="a3120-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="a3120-201">流覽至您已發行的資料夾， **mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64**，然後找出**publish.zip**。</span><span class="sxs-lookup"><span data-stu-id="a3120-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="a3120-202">然後將*publish.zip*上傳至您的 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="a3120-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="a3120-203">您的叢集需要封裝成 jar 檔案的應用程式代碼。</span><span class="sxs-lookup"><span data-stu-id="a3120-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="a3120-204">流覽至您已發行的資料夾**mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64**，然後找出**microsoft-spark-2.3. x-0.3.0。**</span><span class="sxs-lookup"><span data-stu-id="a3120-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="a3120-205">然後，將 jar 檔案上傳到您的 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="a3120-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="a3120-206">可能有多個 .jar 檔案（適用于版本 2.3. x 和 2.4. x 版的 Spark）。</span><span class="sxs-lookup"><span data-stu-id="a3120-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="a3120-207">您必須選擇與叢集建立期間所選擇的 Spark 版本相符的 .jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="a3120-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="a3120-208">例如，如果您在叢集建立期間選擇 Spark 2.3.2，請選擇 [ *microsoft-spark-2.3 x-0.3.0* ]。</span><span class="sxs-lookup"><span data-stu-id="a3120-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="a3120-209">您的叢集需要您應用程式的輸入。</span><span class="sxs-lookup"><span data-stu-id="a3120-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="a3120-210">流覽至您的**mySparkApp**目錄，並找出**input.txt**。</span><span class="sxs-lookup"><span data-stu-id="a3120-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="a3120-211">將您的輸入檔案上傳至 blob 容器中的**使用者/sshuser**目錄。</span><span class="sxs-lookup"><span data-stu-id="a3120-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="a3120-212">您將透過 ssh 連線到您的叢集，而此資料夾是您的叢集尋找其輸入的位置。</span><span class="sxs-lookup"><span data-stu-id="a3120-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="a3120-213">*input.txt*檔案是上傳至特定目錄的唯一檔案。</span><span class="sxs-lookup"><span data-stu-id="a3120-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="a3120-214">執行 HDInsight 腳本動作</span><span class="sxs-lookup"><span data-stu-id="a3120-214">Run the HDInsight script action</span></span>

<span data-ttu-id="a3120-215">一旦您的叢集正在執行，且您已將檔案上傳至 Azure，您就可以在叢集上執行**install-worker.sh**腳本。</span><span class="sxs-lookup"><span data-stu-id="a3120-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="a3120-216">在 Azure 入口網站中，流覽至您的 HDInsight Spark 叢集，然後選取 [**腳本動作**]。</span><span class="sxs-lookup"><span data-stu-id="a3120-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="a3120-217">選取 [ **+ 提交新**的]，並提供下列值：</span><span class="sxs-lookup"><span data-stu-id="a3120-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="a3120-218">屬性</span><span class="sxs-lookup"><span data-stu-id="a3120-218">Property</span></span>  |<span data-ttu-id="a3120-219">描述</span><span class="sxs-lookup"><span data-stu-id="a3120-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="a3120-220">指令碼類型</span><span class="sxs-lookup"><span data-stu-id="a3120-220">Script type</span></span> |<span data-ttu-id="a3120-221">自訂</span><span class="sxs-lookup"><span data-stu-id="a3120-221">Custom</span></span>|
   | <span data-ttu-id="a3120-222">名稱</span><span class="sxs-lookup"><span data-stu-id="a3120-222">Name</span></span> | <span data-ttu-id="a3120-223">安裝背景工作</span><span class="sxs-lookup"><span data-stu-id="a3120-223">Install Worker</span></span>|
   | <span data-ttu-id="a3120-224">Bash 指令碼 URI</span><span class="sxs-lookup"><span data-stu-id="a3120-224">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="a3120-225">若要確認此 URI，請以滑鼠右鍵按一下 Azure 儲存體總管中的 [install-worker.sh]，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a3120-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="a3120-226">節點類型</span><span class="sxs-lookup"><span data-stu-id="a3120-226">Node type(s)</span></span>| <span data-ttu-id="a3120-227">背景工作</span><span class="sxs-lookup"><span data-stu-id="a3120-227">Worker</span></span>|
   | <span data-ttu-id="a3120-228">參數</span><span class="sxs-lookup"><span data-stu-id="a3120-228">Parameters</span></span> | <span data-ttu-id="a3120-229">azure</span><span class="sxs-lookup"><span data-stu-id="a3120-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="a3120-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="a3120-230">/usr/local/bin</span></span>

3. <span data-ttu-id="a3120-231">選取 [**建立**] 以提交您的腳本。</span><span class="sxs-lookup"><span data-stu-id="a3120-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="a3120-232">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a3120-232">Run your app</span></span>

1. <span data-ttu-id="a3120-233">在 Azure 入口網站中，流覽至您的 HDInsight Spark 叢集，然後選取 **[SSH + 叢集登**入]。</span><span class="sxs-lookup"><span data-stu-id="a3120-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="a3120-234">複製 ssh 登入資訊，並將登入貼入終端機。</span><span class="sxs-lookup"><span data-stu-id="a3120-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="a3120-235">使用您在叢集建立期間所設定的密碼來登入您的叢集。</span><span class="sxs-lookup"><span data-stu-id="a3120-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="a3120-236">您應該會看到歡迎您前往 Ubuntu 和 Spark 的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3120-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="a3120-237">使用**spark-submit**命令在 HDInsight 叢集上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3120-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="a3120-238">請記得以您的 blob 容器和儲存體帳戶的實際名稱取代範例腳本中的**mycontainer**和**mystorageaccount** 。</span><span class="sxs-lookup"><span data-stu-id="a3120-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="a3120-239">當您的應用程式執行時，您會看到寫入主控台的「快速入門」本機執行中的相同字數統計表。</span><span class="sxs-lookup"><span data-stu-id="a3120-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="a3120-240">恭喜，您已在雲端中執行 Apache Spark 應用程式的第一個 .NET！</span><span class="sxs-lookup"><span data-stu-id="a3120-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="a3120-241">清除資源</span><span class="sxs-lookup"><span data-stu-id="a3120-241">Clean up resources</span></span>

<span data-ttu-id="a3120-242">HDInsight 會將您的資料儲存在 Azure 儲存體中，因此您可以放心地刪除未使用的叢集。</span><span class="sxs-lookup"><span data-stu-id="a3120-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="a3120-243">您也需支付 HDInsight 叢集的費用 (即使未使用)。</span><span class="sxs-lookup"><span data-stu-id="a3120-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="a3120-244">由於叢集費用是儲存體費用的許多倍，所以刪除未使用的叢集符合經濟效益。</span><span class="sxs-lookup"><span data-stu-id="a3120-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="a3120-245">您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]  。</span><span class="sxs-lookup"><span data-stu-id="a3120-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="a3120-246">刪除資源群組時，會同時刪除 HDInsight Spark 叢集及預設儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="a3120-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3120-247">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a3120-247">Next steps</span></span>

<span data-ttu-id="a3120-248">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="a3120-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="a3120-249">若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。</span><span class="sxs-lookup"><span data-stu-id="a3120-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a3120-250">Azure HDInsight 文件</span><span class="sxs-lookup"><span data-stu-id="a3120-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
