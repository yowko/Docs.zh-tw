---
title: 在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET
description: 瞭解如何在 Azure HDInsight 的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617739"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="20d1c-103">在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="20d1c-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="20d1c-104">本文會教您如何在 Azure HDInsight Spark 叢集上的 Jupyter 筆記本上安裝適用于 Apache Spark 的 .NET。</span><span class="sxs-lookup"><span data-stu-id="20d1c-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="20d1c-105">您可以透過命令列和 Azure 入口網站的組合，在 Azure HDInsight 叢集上部署 Apache Spark 的 .NET （如需詳細資訊，請參閱[如何將適用于 Apache Spark 應用程式的 .net 部署至 Azure HDInsight](../tutorials/hdinsight-deployment.md)），但筆記本提供更具互動性和反復的體驗。</span><span class="sxs-lookup"><span data-stu-id="20d1c-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="20d1c-106">Azure HDInsight 叢集已隨附于 Jupyter 筆記本，因此您只需要設定 Jupyter 筆記本來執行適用于 Apache Spark 的 .NET。</span><span class="sxs-lookup"><span data-stu-id="20d1c-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="20d1c-107">若要在 Jupyter 筆記本中使用 .NET for Apache Spark，需要進行 c # 複寫以逐行執行 c # 程式碼，並在必要時保留執行狀態。</span><span class="sxs-lookup"><span data-stu-id="20d1c-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="20d1c-108">[試用 .net](https://github.com/dotnet/try)已整合為官方的 .net 複寫。</span><span class="sxs-lookup"><span data-stu-id="20d1c-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="20d1c-109">若要透過 Jupyter 筆記本體驗啟用 .NET for Apache Spark，您需要遵循幾個手動步驟，透過[Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari)並在 HDInsight Spark 叢集上提交[腳本動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)。</span><span class="sxs-lookup"><span data-stu-id="20d1c-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="20d1c-110">這項功能是*實驗*性，而且 HDInsight Spark 小組不支援。</span><span class="sxs-lookup"><span data-stu-id="20d1c-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="20d1c-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="20d1c-111">Prerequisites</span></span>

<span data-ttu-id="20d1c-112">如果您還沒有帳戶，請建立一個[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)叢集。</span><span class="sxs-lookup"><span data-stu-id="20d1c-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="20d1c-113">流覽[Azure 入口網站](https://portal.azure.com)，然後選取 [ **+ 建立資源**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="20d1c-114">建立新的 Azure HDInsight 叢集資源。</span><span class="sxs-lookup"><span data-stu-id="20d1c-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="20d1c-115">在叢集建立期間選取 [ **Spark 2.4**和**HDI 4.0** ]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="20d1c-116">安裝適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="20d1c-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="20d1c-117">在 [Azure 入口網站中，選取您在上一個步驟中建立的**HDInsight Spark**叢集。</span><span class="sxs-lookup"><span data-stu-id="20d1c-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="20d1c-118">停止 Livy 伺服器</span><span class="sxs-lookup"><span data-stu-id="20d1c-118">Stop the Livy server</span></span>

1. <span data-ttu-id="20d1c-119">在入口網站中，選取 **[總覽**]，然後選取 [ **Ambari home**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="20d1c-120">如果出現提示，請輸入叢集的登入認證。</span><span class="sxs-lookup"><span data-stu-id="20d1c-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="20d1c-122">從左側導覽功能表中選取 [ **Spark2** ]，然後選取 [ **LIVY FOR Spark2 SERVER**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="20d1c-124">選取 [ **hn0]主機**。</span><span class="sxs-lookup"><span data-stu-id="20d1c-124">Select **hn0... host**.</span></span>

   ![停止 Livy 伺服器](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="20d1c-126">選取 [ **Livy For Spark2 Server** ] 旁的省略號，然後選取 [**停止**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="20d1c-127">出現提示時，選取 **[確定]** 以繼續。</span><span class="sxs-lookup"><span data-stu-id="20d1c-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="20d1c-128">停止 Spark2 伺服器的 Livy。</span><span class="sxs-lookup"><span data-stu-id="20d1c-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="20d1c-129">![停止 Livy 伺服器](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="20d1c-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="20d1c-130">針對 [hn1] 重複上述步驟 ... **主機**。</span><span class="sxs-lookup"><span data-stu-id="20d1c-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="20d1c-131">提交 HDInsight 腳本動作</span><span class="sxs-lookup"><span data-stu-id="20d1c-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="20d1c-132">`install-interactive-notebook.sh`是安裝 .net 進行 Apache Spark 的腳本，並會變更 Apache Livy 和 sparkmagic。</span><span class="sxs-lookup"><span data-stu-id="20d1c-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="20d1c-133">將腳本動作提交至 HDInsight 之前，您必須先建立並上傳 `install-interactive-notebook.sh` 。</span><span class="sxs-lookup"><span data-stu-id="20d1c-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="20d1c-134">在您的本機電腦上建立名為**install-interactive-notebook.sh**的新檔案，並貼上[install-interactive-notebook.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)的內容。</span><span class="sxs-lookup"><span data-stu-id="20d1c-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="20d1c-135">將腳本上傳至可從 HDInsight 叢集存取的[URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 。</span><span class="sxs-lookup"><span data-stu-id="20d1c-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="20d1c-136">例如 `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`。</span><span class="sxs-lookup"><span data-stu-id="20d1c-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="20d1c-137">使用 [HDInsight 指令碼動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-interactive-notebook.sh`。</span><span class="sxs-lookup"><span data-stu-id="20d1c-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="20d1c-138">返回 Azure 入口網站中的 HDI 叢集，然後從左邊的選項中選取 [**腳本動作**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="20d1c-139">您提交一個腳本動作，在 HDInsight Spark 叢集上部署適用于 Apache Spark 複寫的 .NET。</span><span class="sxs-lookup"><span data-stu-id="20d1c-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="20d1c-140">套用下列設定：</span><span class="sxs-lookup"><span data-stu-id="20d1c-140">Use the following settings:</span></span>

   |<span data-ttu-id="20d1c-141">屬性</span><span class="sxs-lookup"><span data-stu-id="20d1c-141">Property</span></span>  |<span data-ttu-id="20d1c-142">描述</span><span class="sxs-lookup"><span data-stu-id="20d1c-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="20d1c-143">指令碼類型</span><span class="sxs-lookup"><span data-stu-id="20d1c-143">Script type</span></span> | <span data-ttu-id="20d1c-144">自訂</span><span class="sxs-lookup"><span data-stu-id="20d1c-144">Custom</span></span> |
   | <span data-ttu-id="20d1c-145">名稱</span><span class="sxs-lookup"><span data-stu-id="20d1c-145">Name</span></span> | <span data-ttu-id="20d1c-146">*安裝適用于 Apache Spark 互動式筆記本體驗的 .NET*</span><span class="sxs-lookup"><span data-stu-id="20d1c-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="20d1c-147">Bash 指令碼 URI</span><span class="sxs-lookup"><span data-stu-id="20d1c-147">Bash script URI</span></span> | <span data-ttu-id="20d1c-148">您上傳 `install-interactive-notebook.sh` 的目標 URI。</span><span class="sxs-lookup"><span data-stu-id="20d1c-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="20d1c-149">節點類型</span><span class="sxs-lookup"><span data-stu-id="20d1c-149">Node type(s)</span></span>| <span data-ttu-id="20d1c-150">前端和背景工作角色</span><span class="sxs-lookup"><span data-stu-id="20d1c-150">Head and Worker</span></span> |
   | <span data-ttu-id="20d1c-151">參數</span><span class="sxs-lookup"><span data-stu-id="20d1c-151">Parameters</span></span> | <span data-ttu-id="20d1c-152">適用于 Apache Spark 版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="20d1c-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="20d1c-153">您可以檢查[.net 的 Apache Spark 版本](https://github.com/dotnet/spark/releases)。</span><span class="sxs-lookup"><span data-stu-id="20d1c-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="20d1c-154">例如，如果您想要安裝 Sparkdotnet 版本0.6.0，則會是 `0.6.0` 。</span><span class="sxs-lookup"><span data-stu-id="20d1c-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="20d1c-155">當腳本動作的狀態旁邊出現綠色核取記號時，移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="20d1c-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="20d1c-156">啟動 Livy 伺服器</span><span class="sxs-lookup"><span data-stu-id="20d1c-156">Start the Livy server</span></span>

<span data-ttu-id="20d1c-157">遵循[停止 Livy 伺服器](#stop-the-livy-server)一節中的指示，**開始**（而不是**停止**）適用于主機的 Livy for Spark2 伺服器**hn0**和**hn1**。</span><span class="sxs-lookup"><span data-stu-id="20d1c-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="20d1c-158">設定 Spark 預設設定</span><span class="sxs-lookup"><span data-stu-id="20d1c-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="20d1c-159">在入口網站中，選取 **[總覽**]，然後選取 [ **Ambari home**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="20d1c-160">出現提示時，輸入叢集的叢集登入認證。</span><span class="sxs-lookup"><span data-stu-id="20d1c-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="20d1c-161">選取**Spark2** [Spark2**和 [** 進行]]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="20d1c-162">然後選取 [**自訂 spark2-預設值**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-162">Then, select **Custom spark2-defaults**.</span></span>

   ![設定配置](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="20d1c-164">選取 [**新增屬性**]，以新增 Spark 預設設定。</span><span class="sxs-lookup"><span data-stu-id="20d1c-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![新增屬性](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="20d1c-166">有三個個別的屬性。</span><span class="sxs-lookup"><span data-stu-id="20d1c-166">There are three individual properties.</span></span> <span data-ttu-id="20d1c-167">使用 [單一屬性] [新增模式] 中的 [ **TEXT** ] 屬性類型，一次新增一個。</span><span class="sxs-lookup"><span data-stu-id="20d1c-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="20d1c-168">檢查任何索引鍵/值前後是否有任何多餘的空格。</span><span class="sxs-lookup"><span data-stu-id="20d1c-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="20d1c-169">**屬性1**</span><span class="sxs-lookup"><span data-stu-id="20d1c-169">**Property 1**</span></span>
       * <span data-ttu-id="20d1c-170">擊鍵&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="20d1c-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="20d1c-171">值: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="20d1c-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="20d1c-172">**屬性 2**使用您在上一個腳本動作中包含的 Apache Spark .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="20d1c-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="20d1c-173">擊鍵&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="20d1c-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="20d1c-174">值: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="20d1c-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="20d1c-175">**屬性3**</span><span class="sxs-lookup"><span data-stu-id="20d1c-175">**Property 3**</span></span>
       * <span data-ttu-id="20d1c-176">擊鍵&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="20d1c-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="20d1c-177">值: `try`</span><span class="sxs-lookup"><span data-stu-id="20d1c-177">Value: `try`</span></span>

   <span data-ttu-id="20d1c-178">例如，下圖會捕捉新增屬性1的設定：</span><span class="sxs-lookup"><span data-stu-id="20d1c-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![設定配置](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="20d1c-180">新增三個屬性後，選取 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="20d1c-181">如果您看到設定建議的警告畫面，請選取 [**無論如何繼續**]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="20d1c-182">重新開機受影響的元件。</span><span class="sxs-lookup"><span data-stu-id="20d1c-182">Restart affected components.</span></span>

   <span data-ttu-id="20d1c-183">加入新的屬性之後，您必須重新開機受變更影響的元件。</span><span class="sxs-lookup"><span data-stu-id="20d1c-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="20d1c-184">在頂端，選取 [**重新開機**]，然後從下拉式選單 [**重新開機所有受影響**的]。</span><span class="sxs-lookup"><span data-stu-id="20d1c-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![設定配置](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="20d1c-186">出現提示時，選取 [**確認全部重新開機**以繼續]，然後按一下 **[確定**] 以完成。</span><span class="sxs-lookup"><span data-stu-id="20d1c-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="20d1c-187">透過 Jupyter 筆記本提交作業</span><span class="sxs-lookup"><span data-stu-id="20d1c-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="20d1c-188">完成先前的步驟之後，您現在可以透過 Jupyter 筆記本提交您的 .NET 以進行 Apache Spark 作業。</span><span class="sxs-lookup"><span data-stu-id="20d1c-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="20d1c-189">為 Apache Spark 筆記本建立新的 .NET。</span><span class="sxs-lookup"><span data-stu-id="20d1c-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="20d1c-190">在 Azure 入口網站中，從您的 HDI 叢集啟動 Jupyter 筆記本。</span><span class="sxs-lookup"><span data-stu-id="20d1c-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![啟動 Jupyter Notebook](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="20d1c-192">然後，選取**New**  >  **[新增 .net Spark （c #）** ] 以建立筆記本。</span><span class="sxs-lookup"><span data-stu-id="20d1c-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="20d1c-194">使用適用于 Apache Spark 的 .NET 提交作業。</span><span class="sxs-lookup"><span data-stu-id="20d1c-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="20d1c-195">使用下列程式碼片段來建立資料框架：</span><span class="sxs-lookup"><span data-stu-id="20d1c-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![提交 Spark 作業](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="20d1c-197">使用下列程式碼片段來註冊使用者定義函式（UDF），並搭配資料框架使用 UDF：</span><span class="sxs-lookup"><span data-stu-id="20d1c-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![提交 Spark 作業](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="20d1c-199">後續步驟</span><span class="sxs-lookup"><span data-stu-id="20d1c-199">Next steps</span></span>

* [<span data-ttu-id="20d1c-200">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="20d1c-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="20d1c-201">HDInsight 檔</span><span class="sxs-lookup"><span data-stu-id="20d1c-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
