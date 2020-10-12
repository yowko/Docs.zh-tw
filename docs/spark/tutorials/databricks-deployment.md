---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1f705878a577a7fa375346cae18010d8c8cc77e1
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955443"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="c2354-103">教學課程：將 Apache Spark 應用程式的 .NET 部署至 Databricks</span><span class="sxs-lookup"><span data-stu-id="c2354-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="c2354-104">本教學課程會指導您如何透過 Azure Databricks （以 Apache Spark 為基礎的分析平臺），將應用程式部署至雲端，並提供單鍵設定、簡化的工作流程，以及啟用共同作業的互動式工作區。</span><span class="sxs-lookup"><span data-stu-id="c2354-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="c2354-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="c2354-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c2354-106">建立 Azure Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="c2354-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="c2354-107">發行您的 .NET 以 Apache Spark 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2354-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="c2354-108">建立 Spark 作業和 Spark 叢集。</span><span class="sxs-lookup"><span data-stu-id="c2354-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="c2354-109">在 Spark 叢集上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2354-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2354-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="c2354-110">Prerequisites</span></span>

<span data-ttu-id="c2354-111">開始之前，請執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="c2354-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="c2354-112">如果您沒有 Azure 帳戶，請建立 [免費帳戶](https://azure.microsoft.com/free/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="c2354-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="c2354-113">登入 [Azure 入口網站](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="c2354-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="c2354-114">[在10分鐘](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)的教學課程中完成 Apache Spark 開始的 .net。</span><span class="sxs-lookup"><span data-stu-id="c2354-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="c2354-115">建立 Azure Databricks 工作區</span><span class="sxs-lookup"><span data-stu-id="c2354-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="c2354-116">本教學課程不適用 **Azure 免費試用版的訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="c2354-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="c2354-117">如果您有免費帳戶，請移至您的設定檔，並將訂用帳戶變更為**隨用隨付**。</span><span class="sxs-lookup"><span data-stu-id="c2354-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="c2354-118">如需詳細資訊，請參閱 [Azure 免費帳戶](https://azure.microsoft.com/free/dotnet/)。</span><span class="sxs-lookup"><span data-stu-id="c2354-118">For more information, see [Azure free account](https://azure.microsoft.com/free/dotnet/).</span></span> <span data-ttu-id="c2354-119">然後，為您所在區域的 vCPU [移除消費限制](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)並[要求增加配額](/azure/azure-supportability/resource-manager-core-quotas-request)。</span><span class="sxs-lookup"><span data-stu-id="c2354-119">Then, [remove the spending limit](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="c2354-120">當您建立 Azure Databricks 工作區時，您可以選取 [試用版 (進階 - 14 天的免費 DBU)]  定價層，讓工作區可免費存取進階 Azure Databricks DBU 14 天。</span><span class="sxs-lookup"><span data-stu-id="c2354-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="c2354-121">在本節中，您會使用 Azure 入口網站建立 Azure Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="c2354-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="c2354-122">在 Azure 入口網站中，選取 [建立資源]   > [分析]   > [Azure Databricks]  。</span><span class="sxs-lookup"><span data-stu-id="c2354-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![在 Azure 入口網站中建立 Azure Databricks 資源](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="c2354-124">在 [Azure Databricks 服務]  底下，提供值以建立 Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="c2354-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="c2354-125">屬性</span><span class="sxs-lookup"><span data-stu-id="c2354-125">Property</span></span>  |<span data-ttu-id="c2354-126">描述</span><span class="sxs-lookup"><span data-stu-id="c2354-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="c2354-127">**工作區名稱**</span><span class="sxs-lookup"><span data-stu-id="c2354-127">**Workspace name**</span></span>     | <span data-ttu-id="c2354-128">提供您 Databricks 工作區的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2354-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="c2354-129">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="c2354-129">**Subscription**</span></span>     | <span data-ttu-id="c2354-130">從下拉式清單中選取您的 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="c2354-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="c2354-131">**資源群組**</span><span class="sxs-lookup"><span data-stu-id="c2354-131">**Resource group**</span></span>     | <span data-ttu-id="c2354-132">指定您是要建立新的資源群組，還是使用現有資源群組。</span><span class="sxs-lookup"><span data-stu-id="c2354-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="c2354-133">資源群組是存放 Azure 方案相關資源的容器。</span><span class="sxs-lookup"><span data-stu-id="c2354-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="c2354-134">如需詳細資訊，請參閱 [Azure 資源群組概觀](/azure/azure-resource-manager/resource-group-overview)。</span><span class="sxs-lookup"><span data-stu-id="c2354-134">For more information, see [Azure Resource Group overview](/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="c2354-135">**位置**</span><span class="sxs-lookup"><span data-stu-id="c2354-135">**Location**</span></span>     | <span data-ttu-id="c2354-136">選取您的慣用區域。</span><span class="sxs-lookup"><span data-stu-id="c2354-136">Select your preferred region.</span></span> <span data-ttu-id="c2354-137">如需可用區域的詳細資訊，請參閱 [依區域提供的 Azure 服務](https://azure.microsoft.com/regions/services/)。</span><span class="sxs-lookup"><span data-stu-id="c2354-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="c2354-138">定價層</span><span class="sxs-lookup"><span data-stu-id="c2354-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="c2354-139">選擇 [標準]、[進階] 或 [試用]。</span><span class="sxs-lookup"><span data-stu-id="c2354-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="c2354-140">如需這些定價層的詳細資訊，請參閱 [Databricks 定價頁面](https://azure.microsoft.com/pricing/details/databricks/)。</span><span class="sxs-lookup"><span data-stu-id="c2354-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="c2354-141">**虛擬網路**</span><span class="sxs-lookup"><span data-stu-id="c2354-141">**Virtual Network**</span></span>     |   <span data-ttu-id="c2354-142">否</span><span class="sxs-lookup"><span data-stu-id="c2354-142">No</span></span>       |

3. <span data-ttu-id="c2354-143">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="c2354-143">Select **Create**.</span></span> <span data-ttu-id="c2354-144">工作區建立需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="c2354-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="c2354-145">在工作區建立期間，您可以在 [通知] 中檢視部署狀態。</span><span class="sxs-lookup"><span data-stu-id="c2354-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="c2354-146">安裝 Azure Databricks 工具</span><span class="sxs-lookup"><span data-stu-id="c2354-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="c2354-147">您可以使用 **DATABRICKS CLI** 來連線到 Azure Databricks 叢集，並從本機電腦將檔案上傳到其中。</span><span class="sxs-lookup"><span data-stu-id="c2354-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="c2354-148">Databricks 叢集會透過 DBFS (Databricks 檔案系統) 存取檔案。</span><span class="sxs-lookup"><span data-stu-id="c2354-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="c2354-149">Databricks CLI 需要 Python 3.6 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c2354-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="c2354-150">如果您已經安裝 Python，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="c2354-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="c2354-151">**若為 Windows：**</span><span class="sxs-lookup"><span data-stu-id="c2354-151">**For Windows:**</span></span>

   [<span data-ttu-id="c2354-152">下載適用于 Windows 的 Python</span><span class="sxs-lookup"><span data-stu-id="c2354-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="c2354-153">**針對 Linux：** Python 已預先安裝在大部分的 Linux 發行版本上。</span><span class="sxs-lookup"><span data-stu-id="c2354-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="c2354-154">執行下列命令以查看您已安裝的版本：</span><span class="sxs-lookup"><span data-stu-id="c2354-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="c2354-155">使用 pip 安裝 Databricks CLI。</span><span class="sxs-lookup"><span data-stu-id="c2354-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="c2354-156">Python 3.4 和更新版本預設包含 pip。</span><span class="sxs-lookup"><span data-stu-id="c2354-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="c2354-157">使用 pip3 for Python 3。</span><span class="sxs-lookup"><span data-stu-id="c2354-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="c2354-158">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c2354-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="c2354-159">安裝 Databricks CLI 之後，請開啟新的命令提示字元，然後執行命令 `databricks` 。</span><span class="sxs-lookup"><span data-stu-id="c2354-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="c2354-160">如果您收到「 **databricks」無法辨識為內部或外部命令的錯誤**，請確定您已開啟新的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c2354-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="c2354-161">設定 Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="c2354-161">Set up Azure Databricks</span></span>

<span data-ttu-id="c2354-162">現在您已安裝 Databricks CLI，您需要設定驗證詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c2354-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="c2354-163">執行 Databricks CLI 命令 `databricks configure --token` 。</span><span class="sxs-lookup"><span data-stu-id="c2354-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="c2354-164">執行設定命令之後，系統會提示您輸入主機。</span><span class="sxs-lookup"><span data-stu-id="c2354-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="c2354-165">您的主機 URL 會使用下列格式： `https://<Location>.azuredatabricks.net` 。</span><span class="sxs-lookup"><span data-stu-id="c2354-165">Your host URL uses the format: `https://<Location>.azuredatabricks.net`.</span></span> <span data-ttu-id="c2354-166">比方說，如果您在 Azure Databricks 服務建立期間選取了 **eastus2** ，主機就會是 `https://eastus2.azuredatabricks.net` 。</span><span class="sxs-lookup"><span data-stu-id="c2354-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be `https://eastus2.azuredatabricks.net`.</span></span>

3. <span data-ttu-id="c2354-167">輸入您的主機之後，系統會提示您輸入權杖。</span><span class="sxs-lookup"><span data-stu-id="c2354-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="c2354-168">在 [Azure 入口網站中，選取 [ **啟動工作區** ] 以啟動您的 Azure Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="c2354-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![啟動 Azure Databricks 工作區](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="c2354-170">在工作區的首頁上，選取 [ **使用者設定**]。</span><span class="sxs-lookup"><span data-stu-id="c2354-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure Databricks 工作區中的使用者設定](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="c2354-172">在 [使用者設定] 頁面上，您可以產生新的權杖。</span><span class="sxs-lookup"><span data-stu-id="c2354-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="c2354-173">複製產生的權杖，並將其貼回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c2354-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![在 Azure Databricks 工作區中產生新的存取權杖](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="c2354-175">您現在應該能夠存取您建立的任何 Azure Databricks 叢集，並將檔案上傳到 DBFS。</span><span class="sxs-lookup"><span data-stu-id="c2354-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="c2354-176">下載背景工作相依性</span><span class="sxs-lookup"><span data-stu-id="c2354-176">Download worker dependencies</span></span>

1. <span data-ttu-id="c2354-177">Apache Spark 可協助執行您的應用程式，例如您可能已撰寫 (Udf) 的任何使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="c2354-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="c2354-178">下載 [Microsoft. 背景工作角色](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="c2354-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="c2354-179">*Install-worker.sh*是可讓您將 Apache Spark 相依檔案的 .net 複製到叢集節點的腳本。</span><span class="sxs-lookup"><span data-stu-id="c2354-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="c2354-180">在您的本機電腦上建立名為 **install-worker.sh** 的新檔案，並貼上位於 GitHub 上的 [install-worker.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) 。</span><span class="sxs-lookup"><span data-stu-id="c2354-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="c2354-181">*Db-init.sh*是將相依性安裝在 Databricks Spark 叢集上的腳本。</span><span class="sxs-lookup"><span data-stu-id="c2354-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="c2354-182">在您的本機電腦上建立名為 **db-init.sh** 的新檔案，並貼上位於 GitHub 上的 [db-init.sh 內容](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 。</span><span class="sxs-lookup"><span data-stu-id="c2354-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="c2354-183">在您剛才建立的檔案中，將 `DOTNET_SPARK_RELEASE` 變數設為 `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz` 。</span><span class="sxs-lookup"><span data-stu-id="c2354-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="c2354-184">將其餘的 *db-init.sh* 檔案保持原狀。</span><span class="sxs-lookup"><span data-stu-id="c2354-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="c2354-185">如果您使用的是 Windows，請確認 *install-worker.sh* 和 *db-init.sh* 腳本中的行尾結束符號為 Unix 樣式 (LF) 。</span><span class="sxs-lookup"><span data-stu-id="c2354-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="c2354-186">您可以透過記事本 + + 和 Atom 等文字編輯器來變更行尾結束符號。</span><span class="sxs-lookup"><span data-stu-id="c2354-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="c2354-187">發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="c2354-187">Publish your app</span></span>

<span data-ttu-id="c2354-188">接下來，您可以在10分鐘的教學課程中發佈在[開始 Apache Spark .net](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)中建立的*mySparkApp* ，以確保您的 Spark 叢集可以存取執行應用程式所需的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="c2354-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="c2354-189">執行下列命令以發佈 *mySparkApp*：</span><span class="sxs-lookup"><span data-stu-id="c2354-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="c2354-190">請執行下列工作來壓縮已發佈的應用程式檔，讓您可以輕鬆地將它們上傳至您的 Databricks Spark 叢集。</span><span class="sxs-lookup"><span data-stu-id="c2354-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="c2354-191">**在 Windows 上：**</span><span class="sxs-lookup"><span data-stu-id="c2354-191">**On Windows:**</span></span>

   <span data-ttu-id="c2354-192">流覽至 mySparkApp/bin/Release/netcoreapp 3.1/ubuntu. 16.04-x64。</span><span class="sxs-lookup"><span data-stu-id="c2354-192">Navigate to mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64.</span></span> <span data-ttu-id="c2354-193">然後，在 [ **發行** 資料夾] 上按一下滑鼠右鍵，然後選取 [ **傳送至 > 壓縮 (壓縮) 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="c2354-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="c2354-194">將新資料夾命名為 **publish.zip**。</span><span class="sxs-lookup"><span data-stu-id="c2354-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="c2354-195">**在 Linux 上，執行下列命令：**</span><span class="sxs-lookup"><span data-stu-id="c2354-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="c2354-196">上傳檔案</span><span class="sxs-lookup"><span data-stu-id="c2354-196">Upload files</span></span>

<span data-ttu-id="c2354-197">在本節中，您會將數個檔案上傳至 DBFS，讓您的叢集擁有在雲端中執行應用程式所需的一切。</span><span class="sxs-lookup"><span data-stu-id="c2354-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="c2354-198">每次您將檔案上傳至 DBFS 時，請確定您位於電腦上該檔案所在的目錄中。</span><span class="sxs-lookup"><span data-stu-id="c2354-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="c2354-199">執行下列命令，將*db-init.sh*、 *install-worker.sh\*\*和 DBFS*上傳至：</span><span class="sxs-lookup"><span data-stu-id="c2354-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="c2354-200">執行下列命令來上傳您的叢集將執行應用程式所需的剩餘檔案：壓縮的發行資料夾、 *input.txt*和 *microsoft-spark-2.4. x-0.3.1 .jar*。</span><span class="sxs-lookup"><span data-stu-id="c2354-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.1.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp publish.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="c2354-201">建立作業</span><span class="sxs-lookup"><span data-stu-id="c2354-201">Create a job</span></span>

<span data-ttu-id="c2354-202">您的應用程式會透過執行 **spark 提交**的作業在 Azure Databricks 上執行，這是您用來執行 .net 以進行 Apache Spark 作業的命令。</span><span class="sxs-lookup"><span data-stu-id="c2354-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="c2354-203">在 Azure Databricks 工作區中，選取 [ **作業** ] 圖示，然後選取 [ **+ 建立作業**]。</span><span class="sxs-lookup"><span data-stu-id="c2354-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![建立 Azure Databricks 作業](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="c2354-205">選擇您作業的標題，然後選取 [ **設定 spark-提交**]。</span><span class="sxs-lookup"><span data-stu-id="c2354-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![設定 spark-提交 Databricks 作業](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="c2354-207">在作業設定中貼上下列參數。</span><span class="sxs-lookup"><span data-stu-id="c2354-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="c2354-208">然後，選取 [ **確認**]。</span><span class="sxs-lookup"><span data-stu-id="c2354-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="c2354-209">建立叢集</span><span class="sxs-lookup"><span data-stu-id="c2354-209">Create a cluster</span></span>

1. <span data-ttu-id="c2354-210">流覽至您的作業，然後選取 [ **編輯** ] 以設定作業的叢集。</span><span class="sxs-lookup"><span data-stu-id="c2354-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="c2354-211">將您的叢集設定為 **Spark 2.4.1**。</span><span class="sxs-lookup"><span data-stu-id="c2354-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="c2354-212">然後，選取 [ **Advanced Options**  >  **Init Scripts**]。</span><span class="sxs-lookup"><span data-stu-id="c2354-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="c2354-213">將 Init 腳本路徑設定為 `dbfs:/spark-dotnet/db-init.sh` 。</span><span class="sxs-lookup"><span data-stu-id="c2354-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![在 Azure Databricks 中設定 spark 叢集](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="c2354-215">選取 [ **確認** ] 以確認您的叢集設定。</span><span class="sxs-lookup"><span data-stu-id="c2354-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="c2354-216">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c2354-216">Run your app</span></span>

1. <span data-ttu-id="c2354-217">流覽至您的作業，然後選取 [ **立即執行** ]，在新設定的 Spark 叢集上執行您的作業。</span><span class="sxs-lookup"><span data-stu-id="c2354-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="c2354-218">建立作業的叢集需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="c2354-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="c2354-219">一旦建立之後，您的作業就會提交，而且您可以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="c2354-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="c2354-220">從 **左側功能表中選取** [叢集]，然後選取 [名稱] 和 [執行您的作業]。</span><span class="sxs-lookup"><span data-stu-id="c2354-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="c2354-221">選取 [ **驅動程式記錄** ] 以查看作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="c2354-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="c2354-222">當您的應用程式完成執行時，您會看到寫入至標準輸出主控台的「開始使用」本機回合中有相同的「字數統計」表格。</span><span class="sxs-lookup"><span data-stu-id="c2354-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks 作業輸出資料表](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="c2354-224">恭喜，您已在雲端中執行 Apache Spark 應用程式的第一個 .NET！</span><span class="sxs-lookup"><span data-stu-id="c2354-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="c2354-225">清除資源</span><span class="sxs-lookup"><span data-stu-id="c2354-225">Clean up resources</span></span>

<span data-ttu-id="c2354-226">如果您不再需要 Databricks 工作區，您可以在 Azure 入口網站中刪除您的 Azure Databricks 資源。</span><span class="sxs-lookup"><span data-stu-id="c2354-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="c2354-227">您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]。</span><span class="sxs-lookup"><span data-stu-id="c2354-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2354-228">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c2354-228">Next steps</span></span>

<span data-ttu-id="c2354-229">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="c2354-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="c2354-230">若要深入了解 Databricks，請繼續前往 Azure Databricks 文件。</span><span class="sxs-lookup"><span data-stu-id="c2354-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c2354-231">Azure Databricks 文件</span><span class="sxs-lookup"><span data-stu-id="c2354-231">Azure Databricks Documentation</span></span>](/azure/azure-databricks/)
