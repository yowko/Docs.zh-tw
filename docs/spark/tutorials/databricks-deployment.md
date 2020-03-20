---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503956"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="f9dbb-103">教程：將用於 Apache Spark 應用程式的 .NET 部署到資料磚塊</span><span class="sxs-lookup"><span data-stu-id="f9dbb-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="f9dbb-104">本教程教您如何通過 Azure 資料磚塊（基於 Apache Spark 的分析平臺）將應用部署到雲中，該平臺具有一鍵式設置、簡化的工作流和互動式工作區，可實現協作。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="f9dbb-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="f9dbb-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f9dbb-106">建立 Azure Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="f9dbb-107">發佈您的 .NET 用於 Apache Spark 應用。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="f9dbb-108">創建 Spark 作業和 Spark 群集。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="f9dbb-109">在 Spark 群集上運行應用。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f9dbb-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="f9dbb-110">Prerequisites</span></span>

<span data-ttu-id="f9dbb-111">在開始之前，執行以下任務：</span><span class="sxs-lookup"><span data-stu-id="f9dbb-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="f9dbb-112">如果沒有 Azure 帳戶，請創建[一個免費帳戶](https://azure.microsoft.com/free/)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="f9dbb-113">登錄到 Azure[門戶](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="f9dbb-114">完成[阿帕奇火花的 .NET - 在 10 分鐘教程中入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="f9dbb-115">建立 Azure Databricks 工作區</span><span class="sxs-lookup"><span data-stu-id="f9dbb-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="f9dbb-116">本教學課程不適用 **Azure 免費試用版的訂用帳戶**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="f9dbb-117">如果您有免費帳戶，請移至您的設定檔，並將訂用帳戶變更為**隨用隨付**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="f9dbb-118">如需詳細資訊，請參閱 [Azure 免費帳戶](https://azure.microsoft.com/free/)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="f9dbb-119">然後，為您所在區域的 vCPU [移除消費限制](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)並[要求增加配額](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="f9dbb-120">當您建立 Azure Databricks 工作區時，您可以選取 [試用版 (進階 - 14 天的免費 DBU)]\*\*\*\* 定價層，讓工作區可免費存取進階 Azure Databricks DBU 14 天。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="f9dbb-121">在本節中，您會使用 Azure 入口網站建立 Azure Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="f9dbb-122">在 Azure 門戶中，選擇 **"創建資源** > **分析** > **Azure 資料塊**"。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![在 Azure 門戶中創建 Azure 資料磚塊資源](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="f9dbb-124">在 [Azure Databricks 服務]\*\*\*\* 底下，提供值以建立 Databricks 工作區。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="f9dbb-125">屬性</span><span class="sxs-lookup"><span data-stu-id="f9dbb-125">Property</span></span>  |<span data-ttu-id="f9dbb-126">描述</span><span class="sxs-lookup"><span data-stu-id="f9dbb-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="f9dbb-127">**工作區名稱**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-127">**Workspace name**</span></span>     | <span data-ttu-id="f9dbb-128">提供您 Databricks 工作區的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="f9dbb-129">**訂閱**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-129">**Subscription**</span></span>     | <span data-ttu-id="f9dbb-130">從下拉式清單中選取您的 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="f9dbb-131">**資源組**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-131">**Resource group**</span></span>     | <span data-ttu-id="f9dbb-132">指定您是要建立新的資源群組，還是使用現有資源群組。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="f9dbb-133">資源群組是存放 Azure 方案相關資源的容器。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="f9dbb-134">如需詳細資訊，請參閱 [Azure 資源群組概觀](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="f9dbb-135">**位置**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-135">**Location**</span></span>     | <span data-ttu-id="f9dbb-136">選取您的慣用區域。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-136">Select your preferred region.</span></span> <span data-ttu-id="f9dbb-137">有關可用區域的資訊，請參閱[按區域提供的 Azure 服務](https://azure.microsoft.com/regions/services/)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="f9dbb-138">**定價層**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="f9dbb-139">選擇 [標準]\*\*\*\*、[進階]\*\*\*\* 或 [試用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="f9dbb-140">如需這些定價層的詳細資訊，請參閱 [Databricks 定價頁面](https://azure.microsoft.com/pricing/details/databricks/)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="f9dbb-141">**虛擬網路**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-141">**Virtual Network**</span></span>     |   <span data-ttu-id="f9dbb-142">否</span><span class="sxs-lookup"><span data-stu-id="f9dbb-142">No</span></span>       |

3. <span data-ttu-id="f9dbb-143">選取 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-143">Select **Create**.</span></span> <span data-ttu-id="f9dbb-144">工作區建立需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="f9dbb-145">在工作區建立期間，您可以在 [通知]\*\*\*\* 中檢視部署狀態。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="f9dbb-146">安裝 Azure 資料磚塊工具</span><span class="sxs-lookup"><span data-stu-id="f9dbb-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="f9dbb-147">可以使用**DataBRICKS CLI**連接到 Azure 資料磚塊群集，並從本地電腦將檔上載到它們。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="f9dbb-148">資料磚群集通過 DBFS（資料磚檔案系統）訪問檔。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="f9dbb-149">資料磚 CLI 需要 Python 3.6 或以上。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="f9dbb-150">如果您已經安裝了 Python，則可以跳過此步驟。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="f9dbb-151">**對於視窗：**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-151">**For Windows:**</span></span>

   [<span data-ttu-id="f9dbb-152">下載適用于 Windows 的 Python</span><span class="sxs-lookup"><span data-stu-id="f9dbb-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="f9dbb-153">**對於 Linux：** Python 預先安裝在大多數 Linux 發行版本上。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="f9dbb-154">運行以下命令以查看已安裝的版本：</span><span class="sxs-lookup"><span data-stu-id="f9dbb-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="f9dbb-155">使用點子安裝資料磚 CLI。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="f9dbb-156">預設情況下，Python 3.4 及更高版本包括點。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="f9dbb-157">對 Python 3 使用 pip3。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="f9dbb-158">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="f9dbb-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="f9dbb-159">安裝 DataBRICKS CLI 後，打開新的命令提示符並運行命令`databricks`。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="f9dbb-160">如果收到 **"資料磚"未識別為內部或外部命令錯誤**，請確保打開新的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="f9dbb-161">設置 Azure 資料塊</span><span class="sxs-lookup"><span data-stu-id="f9dbb-161">Set up Azure Databricks</span></span>

<span data-ttu-id="f9dbb-162">現在，您已經安裝了 DataBRICKS CLI，您需要設置身份驗證詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="f9dbb-163">運行資料磚 CLI`databricks configure --token`命令 。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="f9dbb-164">回合組態命令後，系統將提示您輸入主機。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="f9dbb-165">您的主機 URL 使用格式： **HTTPs：//<_location>.azuredatabricks.net**.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="f9dbb-166">例如，如果在 Azure 資料磚塊服務創建期間選擇了**Eastus2，** 則主機將是**https://eastus2.azuredatabricks.net**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="f9dbb-167">輸入主機後，系統會提示您輸入權杖。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="f9dbb-168">在 Azure 門戶中，選擇 **"啟動工作區"** 以啟動 Azure 資料塊工作區。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![啟動 Azure 資料塊工作區](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="f9dbb-170">在工作區的主頁上，選擇 **"使用者設置**"。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure 資料磚塊工作區中的使用者設置](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="f9dbb-172">在"使用者設置"頁上，可以生成新權杖。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="f9dbb-173">複製生成的權杖並將其粘貼回命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![在 Azure 資料塊工作區中生成新的訪問權杖](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="f9dbb-175">現在，您應該能夠訪問創建的任何 Azure 資料磚塊群集，並將檔上載到 DBFS。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="f9dbb-176">下載輔助角色依賴項</span><span class="sxs-lookup"><span data-stu-id="f9dbb-176">Download worker dependencies</span></span>

1. <span data-ttu-id="f9dbb-177">Microsoft.Spark.Worker 説明 Apache Spark 執行你的應用，例如您可能編寫的任何使用者定義的函數 （UF）。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="f9dbb-178">下載[微軟.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="f9dbb-179">*install-worker.sh*是一個腳本，允許您將 Apache Spark 相關檔的 .NET 複製到群集的節點中。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="f9dbb-180">在本地電腦上創建名為**install-worker.sh**的新檔，並粘貼位於 GitHub 上的[install-worker.sh內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="f9dbb-181">*db-init.sh*是一個腳本，用於將依賴項安裝到 Databricks Spark 群集上。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="f9dbb-182">在本地電腦上創建名為**db-init.sh**的新檔，並粘貼位於 GitHub 上的[db-init.sh內容](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="f9dbb-183">在剛剛創建的檔中，將`DOTNET_SPARK_RELEASE`變數設置為`https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="f9dbb-184">保留*db-init.sh*檔的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="f9dbb-185">如果使用 Windows，請驗證*install-worker.sh*和*db-init.sh*腳本中的行尾是否為 Unix 樣式 （LF）。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="f9dbb-186">您可以通過文字編輯器（如記事本\* 和 Atom）更改行尾。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="f9dbb-187">發佈您的應用程式</span><span class="sxs-lookup"><span data-stu-id="f9dbb-187">Publish your app</span></span>

<span data-ttu-id="f9dbb-188">接下來，發佈在 .NET 中創建的[mySparkApp，用於 Apache Spark - 在 10 分鐘內入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程，以確保 Spark 群集有權訪問運行應用所需的所有檔。 *mySparkApp*</span><span class="sxs-lookup"><span data-stu-id="f9dbb-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="f9dbb-189">運行以下命令以發佈*mySparkApp*：</span><span class="sxs-lookup"><span data-stu-id="f9dbb-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="f9dbb-190">執行以下任務來壓縮已發佈的應用檔，以便可以輕鬆地將它們上載到 Databricks Spark 群集。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="f9dbb-191">**在 Windows 上：**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-191">**On Windows:**</span></span>

   <span data-ttu-id="f9dbb-192">導航到 mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-192">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="f9dbb-193">然後，按右鍵 **"發佈**"資料夾，然後選擇"**發送到>壓縮（壓縮）資料夾**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="f9dbb-194">為新資料夾**publish.zip 命名**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="f9dbb-195">**在 Linux 上，運行以下命令：**</span><span class="sxs-lookup"><span data-stu-id="f9dbb-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="f9dbb-196">上傳檔案</span><span class="sxs-lookup"><span data-stu-id="f9dbb-196">Upload files</span></span>

<span data-ttu-id="f9dbb-197">在本節中，您將多個檔上載到 DBFS，以便群集擁有在雲中運行應用所需的一切。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="f9dbb-198">每次將檔上載到 DBFS 時，請確保位於該檔位於電腦上的目錄中。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="f9dbb-199">運行以下命令以上載*db-init.sh、install-worker.sh*和*Microsoft.Spark.Worker*到 DBFS： *install-worker.sh*</span><span class="sxs-lookup"><span data-stu-id="f9dbb-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="f9dbb-200">運行以下命令以上載群集運行應用所需的其餘檔：壓縮的發佈資料夾 *、input.txt*和*Microsoft-spark-2.4.x-0.3.0.jar*。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="f9dbb-201">建立作業</span><span class="sxs-lookup"><span data-stu-id="f9dbb-201">Create a job</span></span>

<span data-ttu-id="f9dbb-202">你的應用通過運行**spark-提交**的作業在 Azure Databricks 上運行 ，這是用於為 Apache Spark 作業運行 .NET 的命令。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="f9dbb-203">在 Azure 資料塊工作區中，選擇**作業**圖示，然後 **+ 創建作業**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![創建 Azure 資料磚塊作業](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="f9dbb-205">為作業選擇標題，然後選擇 **"配置火花提交**"。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![為數據磚塊作業配置火花提交](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="f9dbb-207">在作業配置中粘貼以下參數。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="f9dbb-208">然後，選擇 **"確認**"。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="f9dbb-209">建立叢集</span><span class="sxs-lookup"><span data-stu-id="f9dbb-209">Create a cluster</span></span>

1. <span data-ttu-id="f9dbb-210">導航到作業並選擇 **"編輯"** 以配置作業的群集。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="f9dbb-211">將群集設置為**Spark 2.4.1**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="f9dbb-212">然後，選擇**高級選項** > **Init 腳本**。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="f9dbb-213">將 Init 腳本`dbfs:/spark-dotnet/db-init.sh`路徑設置為 。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![在 Azure 資料塊中配置火花群集](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="f9dbb-215">選擇 **"確認**"以確認群集設置。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="f9dbb-216">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="f9dbb-216">Run your app</span></span>

1. <span data-ttu-id="f9dbb-217">導航到作業，然後選擇 **"立即運行"** 以在新配置的 Spark 群集上運行作業。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="f9dbb-218">創建作業的群集需要幾分鐘時間。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="f9dbb-219">創建作業後，將提交作業，您可以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="f9dbb-220">從左側功能表中選擇 **"群集**"，然後選擇作業的名稱和運行。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="f9dbb-221">選擇**驅動程式日誌**以查看作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="f9dbb-222">應用完成執行後，您將看到從已啟動的本地運行中寫入標準輸出主控台的相同字計數表。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure 資料磚塊作業輸出表](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="f9dbb-224">恭喜您，您已經運行了第一個 .NET 在雲中的 Apache Spark 應用程式！</span><span class="sxs-lookup"><span data-stu-id="f9dbb-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="f9dbb-225">清除資源</span><span class="sxs-lookup"><span data-stu-id="f9dbb-225">Clean up resources</span></span>

<span data-ttu-id="f9dbb-226">如果不再需要 DataBRICKS 工作區，則可以在 Azure 門戶中刪除 Azure 資料磚塊資源。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="f9dbb-227">您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9dbb-228">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f9dbb-228">Next steps</span></span>

<span data-ttu-id="f9dbb-229">在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="f9dbb-230">若要深入了解 Databricks，請繼續前往 Azure Databricks 文件。</span><span class="sxs-lookup"><span data-stu-id="f9dbb-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9dbb-231">Azure Databricks 文件</span><span class="sxs-lookup"><span data-stu-id="f9dbb-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
