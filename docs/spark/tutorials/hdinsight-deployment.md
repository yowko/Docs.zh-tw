---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 HDInsight。
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504173"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="65a02-103">教程：將用於 Apache Spark 應用程式的 .NET 部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="65a02-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="65a02-104">本教程將介紹如何通過 Azure HDInsight 群集將 .NET 用於 Apache Spark 應用部署到雲中。</span><span class="sxs-lookup"><span data-stu-id="65a02-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="65a02-105">HDInsight 使在 Azure 中創建和配置 Spark 群集變得更加容易，因為 HDInsight 中的 Spark 群集與 Azure 存儲和 Azure 資料湖存儲相容。</span><span class="sxs-lookup"><span data-stu-id="65a02-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="65a02-106">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="65a02-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="65a02-107">使用 Azure 存儲資源管理器訪問存儲帳戶。</span><span class="sxs-lookup"><span data-stu-id="65a02-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="65a02-108">創建 Azure HDInsight 群集。</span><span class="sxs-lookup"><span data-stu-id="65a02-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="65a02-109">發佈您的 .NET 用於 Apache Spark 應用。</span><span class="sxs-lookup"><span data-stu-id="65a02-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="65a02-110">創建並運行 HDInsight 腳本操作。</span><span class="sxs-lookup"><span data-stu-id="65a02-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="65a02-111">在 HDInsight 群集上運行 Apache Spark 應用的 .NET。</span><span class="sxs-lookup"><span data-stu-id="65a02-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65a02-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="65a02-112">Prerequisites</span></span>

<span data-ttu-id="65a02-113">在開始之前，執行以下任務：</span><span class="sxs-lookup"><span data-stu-id="65a02-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="65a02-114">如果沒有 Azure 訂閱，請創建[一個免費帳戶](https://azure.microsoft.com/free/)。</span><span class="sxs-lookup"><span data-stu-id="65a02-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="65a02-115">登錄到 Azure[門戶](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="65a02-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="65a02-116">在[Windows、Linux](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)或[Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)[MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)電腦上安裝 Azure 存儲資源管理器。</span><span class="sxs-lookup"><span data-stu-id="65a02-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="65a02-117">完成[阿帕奇火花的 .NET - 在 10 分鐘教程中入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)。</span><span class="sxs-lookup"><span data-stu-id="65a02-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="65a02-118">訪問存儲帳戶</span><span class="sxs-lookup"><span data-stu-id="65a02-118">Access your storage accounts</span></span>

1. <span data-ttu-id="65a02-119">開啟 [Azure 儲存體總管]。</span><span class="sxs-lookup"><span data-stu-id="65a02-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="65a02-120">選擇左側功能表上**的"添加帳戶**"，然後登錄到 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="65a02-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![從存儲資源管理器登錄到 Azure 帳戶](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="65a02-122">登錄後，應查看您擁有的所有存儲帳戶以及已上載到存儲帳戶的任何資源。</span><span class="sxs-lookup"><span data-stu-id="65a02-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="65a02-123">建立 HDInsight 叢集</span><span class="sxs-lookup"><span data-stu-id="65a02-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65a02-124">即使不使用 HDInsight 群集，也會每分鐘按比例計費。</span><span class="sxs-lookup"><span data-stu-id="65a02-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="65a02-125">請務必在使用完叢集後將其刪除。</span><span class="sxs-lookup"><span data-stu-id="65a02-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="65a02-126">有關詳細資訊，請參閱本教程的["清理資源](#clean-up-resources)"部分。</span><span class="sxs-lookup"><span data-stu-id="65a02-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="65a02-127">訪問[Azure 門戶](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="65a02-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="65a02-128">選擇 **= 創建資源**。</span><span class="sxs-lookup"><span data-stu-id="65a02-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="65a02-129">然後，從 **"分析"** 類別中選擇**HDInsight。**</span><span class="sxs-lookup"><span data-stu-id="65a02-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![從 Azure 門戶創建 HDInsight 資源](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="65a02-131">在 [基本]\*\*\*\* 下方，提供下列值：</span><span class="sxs-lookup"><span data-stu-id="65a02-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="65a02-132">屬性</span><span class="sxs-lookup"><span data-stu-id="65a02-132">Property</span></span>  |<span data-ttu-id="65a02-133">描述</span><span class="sxs-lookup"><span data-stu-id="65a02-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="65a02-134">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="65a02-134">Subscription</span></span>  | <span data-ttu-id="65a02-135">在下拉清單中，選擇一個活動 Azure 訂閱。</span><span class="sxs-lookup"><span data-stu-id="65a02-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="65a02-136">資源群組</span><span class="sxs-lookup"><span data-stu-id="65a02-136">Resource group</span></span> | <span data-ttu-id="65a02-137">指定您是要建立新的資源群組，還是使用現有資源群組。</span><span class="sxs-lookup"><span data-stu-id="65a02-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="65a02-138">資源群組是存放 Azure 方案相關資源的容器。</span><span class="sxs-lookup"><span data-stu-id="65a02-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="65a02-139">叢集名稱</span><span class="sxs-lookup"><span data-stu-id="65a02-139">Cluster name</span></span> | <span data-ttu-id="65a02-140">提供 HDInsight Spark 叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="65a02-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="65a02-141">Location</span><span class="sxs-lookup"><span data-stu-id="65a02-141">Location</span></span>   | <span data-ttu-id="65a02-142">選取資源群組的位置。</span><span class="sxs-lookup"><span data-stu-id="65a02-142">Select a location for the resource group.</span></span> <span data-ttu-id="65a02-143">此範本會使用這個位置，用於建立叢集以及預設叢集儲存體。</span><span class="sxs-lookup"><span data-stu-id="65a02-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="65a02-144">叢集類型</span><span class="sxs-lookup"><span data-stu-id="65a02-144">Cluster type</span></span>| <span data-ttu-id="65a02-145">選取 [spark]\*\*\*\* 作為叢集類型。</span><span class="sxs-lookup"><span data-stu-id="65a02-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="65a02-146">叢集版本</span><span class="sxs-lookup"><span data-stu-id="65a02-146">Cluster version</span></span>|<span data-ttu-id="65a02-147">選擇群集類型後，此欄位將自動填滿預設版本。</span><span class="sxs-lookup"><span data-stu-id="65a02-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="65a02-148">選擇 2.3 或 2.4 版本的 Spark。</span><span class="sxs-lookup"><span data-stu-id="65a02-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="65a02-149">叢集登入使用者名稱</span><span class="sxs-lookup"><span data-stu-id="65a02-149">Cluster login username</span></span>| <span data-ttu-id="65a02-150">輸入叢集登入使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="65a02-150">Enter the cluster login username.</span></span>  <span data-ttu-id="65a02-151">預設名稱為 *admin*。</span><span class="sxs-lookup"><span data-stu-id="65a02-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="65a02-152">叢集登入密碼</span><span class="sxs-lookup"><span data-stu-id="65a02-152">Cluster login password</span></span>| <span data-ttu-id="65a02-153">輸入任何登錄密碼。</span><span class="sxs-lookup"><span data-stu-id="65a02-153">Enter any login password.</span></span> |
    |<span data-ttu-id="65a02-154">安全殼層 (SSH) 使用者名稱</span><span class="sxs-lookup"><span data-stu-id="65a02-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="65a02-155">輸入 SSH 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="65a02-155">Enter the SSH username.</span></span> <span data-ttu-id="65a02-156">根據預設，此帳戶會共用與「叢集登入使用者名稱」\*\* 帳戶相同的密碼。</span><span class="sxs-lookup"><span data-stu-id="65a02-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="65a02-157">選擇 **"下一步："存儲 >>** 以繼續訪問 **"存儲**"頁。</span><span class="sxs-lookup"><span data-stu-id="65a02-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="65a02-158">在 [儲存體]\*\*\*\* 下方，提供下列值：</span><span class="sxs-lookup"><span data-stu-id="65a02-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="65a02-159">屬性</span><span class="sxs-lookup"><span data-stu-id="65a02-159">Property</span></span>  |<span data-ttu-id="65a02-160">描述</span><span class="sxs-lookup"><span data-stu-id="65a02-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="65a02-161">主要儲存體類型</span><span class="sxs-lookup"><span data-stu-id="65a02-161">Primary storage type</span></span>|<span data-ttu-id="65a02-162">使用預設值 [Azure 儲存體]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65a02-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="65a02-163">選取方法</span><span class="sxs-lookup"><span data-stu-id="65a02-163">Selection method</span></span>|<span data-ttu-id="65a02-164">使用預設值 [從清單中選取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65a02-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="65a02-165">主要儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="65a02-165">Primary storage account</span></span>|<span data-ttu-id="65a02-166">選擇訂閱以及該訂閱中的一個活動存儲帳戶。</span><span class="sxs-lookup"><span data-stu-id="65a02-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="65a02-167">容器</span><span class="sxs-lookup"><span data-stu-id="65a02-167">Container</span></span>|<span data-ttu-id="65a02-168">此容器是存儲帳戶中的特定 Blob 容器，群集在其中查找在雲中運行應用的檔。</span><span class="sxs-lookup"><span data-stu-id="65a02-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="65a02-169">您可以給它任何可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="65a02-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="65a02-170">在 [檢閱 + 建立]\*\*\*\* 底下，選取 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65a02-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="65a02-171">大約需要 20 分鐘的時間來建立叢集。</span><span class="sxs-lookup"><span data-stu-id="65a02-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="65a02-172">必須先創建群集，然後才能繼續執行下一步。</span><span class="sxs-lookup"><span data-stu-id="65a02-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="65a02-173">發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="65a02-173">Publish your app</span></span>

<span data-ttu-id="65a02-174">接下來，發佈在 .NET 中創建的[mySparkApp，用於 Apache Spark - 在 10 分鐘內入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程，該教程允許 Spark 群集訪問運行應用所需的所有檔。 *mySparkApp*</span><span class="sxs-lookup"><span data-stu-id="65a02-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="65a02-175">運行以下命令以發佈*mySparkApp*：</span><span class="sxs-lookup"><span data-stu-id="65a02-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="65a02-176">**在 Windows 上：**</span><span class="sxs-lookup"><span data-stu-id="65a02-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="65a02-177">**在 Linux 上：**</span><span class="sxs-lookup"><span data-stu-id="65a02-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="65a02-178">執行以下任務來壓縮已發佈的應用檔，以便可以輕鬆地將它們上載到 HDInsight 群集。</span><span class="sxs-lookup"><span data-stu-id="65a02-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="65a02-179">**在 Windows 上：**</span><span class="sxs-lookup"><span data-stu-id="65a02-179">**On Windows:**</span></span>

   <span data-ttu-id="65a02-180">導航到*mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64*。</span><span class="sxs-lookup"><span data-stu-id="65a02-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="65a02-181">然後，按右鍵 **"發佈**"資料夾，然後選擇"**發送到>壓縮（壓縮）資料夾**。</span><span class="sxs-lookup"><span data-stu-id="65a02-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="65a02-182">為新資料夾**publish.zip 命名**。</span><span class="sxs-lookup"><span data-stu-id="65a02-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="65a02-183">**在 Linux 上，運行以下命令：**</span><span class="sxs-lookup"><span data-stu-id="65a02-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="65a02-184">將檔上載到 Azure</span><span class="sxs-lookup"><span data-stu-id="65a02-184">Upload files to Azure</span></span>

<span data-ttu-id="65a02-185">接下來，使用 Azure 存儲資源管理器將以下五個檔上載到為群集存儲選擇的 Blob 容器：</span><span class="sxs-lookup"><span data-stu-id="65a02-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="65a02-186">微軟.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="65a02-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="65a02-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="65a02-187">install-worker.sh</span></span>
* <span data-ttu-id="65a02-188">發佈.zip</span><span class="sxs-lookup"><span data-stu-id="65a02-188">publish.zip</span></span>
* <span data-ttu-id="65a02-189">微軟火花-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="65a02-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="65a02-190">輸入.txt.</span><span class="sxs-lookup"><span data-stu-id="65a02-190">input.txt.</span></span>

1. <span data-ttu-id="65a02-191">打開 Azure 存儲資源管理器，並從左側功能表導航到存儲帳戶。</span><span class="sxs-lookup"><span data-stu-id="65a02-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="65a02-192">向下切入到存儲帳戶中的 Blob**容器**下的群集 Blob 容器。</span><span class="sxs-lookup"><span data-stu-id="65a02-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="65a02-193">*Microsoft.Spark.Worker*説明 Apache Spark 執行你的應用，例如您可能編寫的任何使用者定義的函數 （UF）。</span><span class="sxs-lookup"><span data-stu-id="65a02-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="65a02-194">下載[微軟.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="65a02-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="65a02-195">然後，選擇 **"在**Azure 存儲資源管理器中上載"以上載輔助角色。</span><span class="sxs-lookup"><span data-stu-id="65a02-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![將檔上載到 Azure 存儲資源管理器](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="65a02-197">*install-worker.sh*是一個腳本，允許您將 Apache Spark 相關檔的 .NET 複製到群集的節點中。</span><span class="sxs-lookup"><span data-stu-id="65a02-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="65a02-198">創建名為**install-worker.sh**本地電腦的新檔，並粘貼位於 GitHub 上的[install-worker.sh內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。</span><span class="sxs-lookup"><span data-stu-id="65a02-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="65a02-199">然後，將*install-worker.sh*上載到 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="65a02-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="65a02-200">群集需要包含應用已發佈的檔的 publish.ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="65a02-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="65a02-201">導航到已發佈的資料夾 **，mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64**，並找到**發佈.zip**.</span><span class="sxs-lookup"><span data-stu-id="65a02-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="65a02-202">然後上載*Publish.zip*到 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="65a02-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="65a02-203">群集需要打包到 jar 檔中的應用程式代碼。</span><span class="sxs-lookup"><span data-stu-id="65a02-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="65a02-204">導航到您已發佈的資料夾 **，mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64**，並找到**微軟-spark-2.3.x-0.3.0.jar**。</span><span class="sxs-lookup"><span data-stu-id="65a02-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="65a02-205">然後，將 jar 檔上載到 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="65a02-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="65a02-206">可能有多個 .jar 檔（對於 Spark 的版本 2.3.x 和 2.4.x）。</span><span class="sxs-lookup"><span data-stu-id="65a02-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="65a02-207">您需要選擇與群集創建期間選擇的 Spark 版本相匹配的 .jar 檔。</span><span class="sxs-lookup"><span data-stu-id="65a02-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="65a02-208">例如，如果在群集創建期間選擇 Spark 2.3.2，請選擇*Microsoft-spark-2.3.x-0.3.0.jar。*</span><span class="sxs-lookup"><span data-stu-id="65a02-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="65a02-209">群集需要輸入到應用。</span><span class="sxs-lookup"><span data-stu-id="65a02-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="65a02-210">導航到您的**mySparkApp**目錄並找到**輸入.txt**。</span><span class="sxs-lookup"><span data-stu-id="65a02-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="65a02-211">將輸入檔上載到 blob 容器中的**使用者/sshuser**目錄。</span><span class="sxs-lookup"><span data-stu-id="65a02-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="65a02-212">您將通過 ssh 連接到群集，此資料夾是群集查找其輸入的位置。</span><span class="sxs-lookup"><span data-stu-id="65a02-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="65a02-213">*input.txt*檔是唯一上載到特定目錄的檔。</span><span class="sxs-lookup"><span data-stu-id="65a02-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="65a02-214">運行 HDInsight 腳本操作</span><span class="sxs-lookup"><span data-stu-id="65a02-214">Run the HDInsight script action</span></span>

<span data-ttu-id="65a02-215">群集運行並將檔上載到 Azure 後，在群集上運行**install-worker.sh**腳本。</span><span class="sxs-lookup"><span data-stu-id="65a02-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="65a02-216">導航到 Azure 門戶中的 HDInsight Spark 群集，然後選擇**腳本操作**。</span><span class="sxs-lookup"><span data-stu-id="65a02-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="65a02-217">選擇 **= 提交新**值並提供以下值：</span><span class="sxs-lookup"><span data-stu-id="65a02-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="65a02-218">屬性</span><span class="sxs-lookup"><span data-stu-id="65a02-218">Property</span></span>  |<span data-ttu-id="65a02-219">描述</span><span class="sxs-lookup"><span data-stu-id="65a02-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="65a02-220">指令碼類型</span><span class="sxs-lookup"><span data-stu-id="65a02-220">Script type</span></span> |<span data-ttu-id="65a02-221">Custom</span><span class="sxs-lookup"><span data-stu-id="65a02-221">Custom</span></span>|
   | <span data-ttu-id="65a02-222">名稱</span><span class="sxs-lookup"><span data-stu-id="65a02-222">Name</span></span> | <span data-ttu-id="65a02-223">安裝輔助角色</span><span class="sxs-lookup"><span data-stu-id="65a02-223">Install Worker</span></span>|
   | <span data-ttu-id="65a02-224">Bash 指令碼 URI</span><span class="sxs-lookup"><span data-stu-id="65a02-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="65a02-225">要確認此 URI，請按右鍵 Azure 存儲資源管理器中的install-worker.sh並選擇屬性。</span><span class="sxs-lookup"><span data-stu-id="65a02-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="65a02-226">節點類型</span><span class="sxs-lookup"><span data-stu-id="65a02-226">Node type(s)</span></span>| <span data-ttu-id="65a02-227">背景工作</span><span class="sxs-lookup"><span data-stu-id="65a02-227">Worker</span></span>|
   | <span data-ttu-id="65a02-228">參數</span><span class="sxs-lookup"><span data-stu-id="65a02-228">Parameters</span></span> | <span data-ttu-id="65a02-229">azure</span><span class="sxs-lookup"><span data-stu-id="65a02-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="65a02-230">/usr/本地/箱</span><span class="sxs-lookup"><span data-stu-id="65a02-230">/usr/local/bin</span></span>

3. <span data-ttu-id="65a02-231">選擇 **"創建**"以提交腳本。</span><span class="sxs-lookup"><span data-stu-id="65a02-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="65a02-232">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="65a02-232">Run your app</span></span>

1. <span data-ttu-id="65a02-233">導航到 Azure 門戶中的 HDInsight Spark 群集，然後選擇**SSH + 群集登錄**。</span><span class="sxs-lookup"><span data-stu-id="65a02-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="65a02-234">複製 ssh 登錄資訊並將登錄粘貼到終端中。</span><span class="sxs-lookup"><span data-stu-id="65a02-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="65a02-235">使用在群集創建期間設置的密碼登錄到群集。</span><span class="sxs-lookup"><span data-stu-id="65a02-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="65a02-236">您應該會看到歡迎您訪問 Ubuntu 和 Spark 的消息。</span><span class="sxs-lookup"><span data-stu-id="65a02-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="65a02-237">使用**火花提交**命令在 HDInsight 群集上運行應用。</span><span class="sxs-lookup"><span data-stu-id="65a02-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="65a02-238">請記住，在示例腳本中用 blob 容器和存儲帳戶的實際名稱替換**我的容器**和**我的存儲帳戶**。</span><span class="sxs-lookup"><span data-stu-id="65a02-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="65a02-239">應用運行時，您會看到從已啟動的本地運行中寫入主控台的相同字計數表。</span><span class="sxs-lookup"><span data-stu-id="65a02-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="65a02-240">恭喜您，您已經運行了第一個 .NET 在雲中的 Apache Spark 應用程式！</span><span class="sxs-lookup"><span data-stu-id="65a02-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="65a02-241">清除資源</span><span class="sxs-lookup"><span data-stu-id="65a02-241">Clean up resources</span></span>

<span data-ttu-id="65a02-242">HDInsight 將資料保存在 Azure 存儲中，因此您可以安全地刪除群集時未使用。</span><span class="sxs-lookup"><span data-stu-id="65a02-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="65a02-243">您也需支付 HDInsight 叢集的費用 (即使未使用)。</span><span class="sxs-lookup"><span data-stu-id="65a02-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="65a02-244">由於叢集費用是儲存體費用的許多倍，所以刪除未使用的叢集符合經濟效益。</span><span class="sxs-lookup"><span data-stu-id="65a02-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="65a02-245">您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65a02-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="65a02-246">刪除資源群組時，會同時刪除 HDInsight Spark 叢集及預設儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="65a02-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="65a02-247">後續步驟</span><span class="sxs-lookup"><span data-stu-id="65a02-247">Next steps</span></span>

<span data-ttu-id="65a02-248">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。</span><span class="sxs-lookup"><span data-stu-id="65a02-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="65a02-249">若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。</span><span class="sxs-lookup"><span data-stu-id="65a02-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="65a02-250">Azure HDInsight 文檔</span><span class="sxs-lookup"><span data-stu-id="65a02-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
