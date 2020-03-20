---
title: 在 Azure HDInsight Spark 群集上的 Jupyter 筆記本電腦上安裝用於 Apache Spark 的 NET
description: 瞭解如何在 Azure HDInsight 的 Jupyter 筆記本上安裝用於 Apache Spark 的 .NET。
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 32047efcde093a3752bdd59baa88896d1547b93e
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546746"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="7f05c-103">在 Azure HDInsight Spark 群集上的 Jupyter 筆記本電腦上安裝用於 Apache Spark 的 NET</span><span class="sxs-lookup"><span data-stu-id="7f05c-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="7f05c-104">本文教您如何在 Azure HDInsight Spark 群集上的 Jupyter 筆記本電腦上安裝用於 Apache Spark 的 .NET。</span><span class="sxs-lookup"><span data-stu-id="7f05c-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="7f05c-105">您可以通過命令列和 Azure 門戶的組合在 Azure HDInsight 群集上部署 A奇星（有關詳細資訊，請參閱[如何將 .NET 用於 Apache Spark 的應用程式部署到 Azure HDInsight），](../tutorials/hdinsight-deployment.md)但筆記本可提供更具交互性和反覆運算性的體驗。</span><span class="sxs-lookup"><span data-stu-id="7f05c-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="7f05c-106">Azure HDInsight 群集已經附帶了 Jupyter 筆記本，因此您所要做的就是將 Jupyter 筆記本配置為運行的 .NET 以用於 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="7f05c-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="7f05c-107">要在 Jupyter 筆記本中使用用於 Apache Spark 的 .NET，需要 C# REPL 逐行執行 C# 代碼，並在必要時保留執行狀態。</span><span class="sxs-lookup"><span data-stu-id="7f05c-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="7f05c-108">[try .NET](https://github.com/dotnet/try)已集成為官方 .NET REPL。</span><span class="sxs-lookup"><span data-stu-id="7f05c-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="7f05c-109">要通過 Jupyter 筆記本體驗啟用 .NET 阿帕奇火花，您需要在[Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari)中執行幾個手動步驟，並在 HDInsight Spark 群集上提交[腳本操作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)。</span><span class="sxs-lookup"><span data-stu-id="7f05c-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="7f05c-110">此功能是*實驗性*的，HDInsight Spark 團隊不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="7f05c-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f05c-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="7f05c-111">Prerequisites</span></span>

<span data-ttu-id="7f05c-112">如果還沒有，請創建[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster)群集。</span><span class="sxs-lookup"><span data-stu-id="7f05c-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster) cluster.</span></span>

1. <span data-ttu-id="7f05c-113">訪問[Azure 門戶](https://portal.azure.com)並選擇 **" 創建資源**"。</span><span class="sxs-lookup"><span data-stu-id="7f05c-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="7f05c-114">創建新的 Azure HDInsight 群集資源。</span><span class="sxs-lookup"><span data-stu-id="7f05c-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="7f05c-115">在群集創建期間選擇**Spark 2.4**和**HDI 4.0。**</span><span class="sxs-lookup"><span data-stu-id="7f05c-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="7f05c-116">安裝 .NET 用於阿帕奇火花</span><span class="sxs-lookup"><span data-stu-id="7f05c-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="7f05c-117">在 Azure 門戶中，選擇您在上一步中創建的**HDInsight Spark 群集**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="7f05c-118">停止利維伺服器</span><span class="sxs-lookup"><span data-stu-id="7f05c-118">Stop the Livy server</span></span>

1. <span data-ttu-id="7f05c-119">從門戶中，選擇 **"概述**"，然後選擇**Ambari 主頁**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="7f05c-120">如果出現提示，請輸入群集的登錄憑據。</span><span class="sxs-lookup"><span data-stu-id="7f05c-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![停止利維伺服器](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="7f05c-122">從左側導航功能表中選擇**Spark2，** 然後選擇**SPARK2 伺服器的 LIVY。**</span><span class="sxs-lookup"><span data-stu-id="7f05c-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![停止利維伺服器](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="7f05c-124">選擇**hn0...主機**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-124">Select **hn0... host**.</span></span>

   ![停止利維伺服器](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="7f05c-126">為**Spark2 伺服器選擇 Livy**旁邊的省略號，然後選擇 **"停止**"。</span><span class="sxs-lookup"><span data-stu-id="7f05c-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="7f05c-127">當出現提示時，選擇 **"確定**"以繼續。</span><span class="sxs-lookup"><span data-stu-id="7f05c-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="7f05c-128">停止 Spark2 伺服器的利維。</span><span class="sxs-lookup"><span data-stu-id="7f05c-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="7f05c-129">![停止利維伺服器](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="7f05c-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="7f05c-130">重複**hn1 的上述步驟...主機**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="7f05c-131">提交 HDInsight 腳本操作</span><span class="sxs-lookup"><span data-stu-id="7f05c-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="7f05c-132">是`install-interactive-notebook.sh`一個腳本，安裝 .NET 為 Apache Spark，並作出更改阿帕奇利維和火花魔術。</span><span class="sxs-lookup"><span data-stu-id="7f05c-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="7f05c-133">在將腳本操作提交到 HDInsight 之前，您需要創建和上載`install-interactive-notebook.sh`。</span><span class="sxs-lookup"><span data-stu-id="7f05c-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="7f05c-134">在本地電腦中創建名為**install-interactive-notebook.sh**的新檔，並粘貼[install-interactive-notebook.sh內容的內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)。</span><span class="sxs-lookup"><span data-stu-id="7f05c-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="7f05c-135">將腳本上載到可從 HDInsight 群集訪問的[URI。](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions)</span><span class="sxs-lookup"><span data-stu-id="7f05c-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="7f05c-136">例如： `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh` 。</span><span class="sxs-lookup"><span data-stu-id="7f05c-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="7f05c-137">使用 [HDInsight 指令碼動作](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)在叢集上執行 `install-interactive-notebook.sh`。</span><span class="sxs-lookup"><span data-stu-id="7f05c-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="7f05c-138">返回到 Azure 門戶中的 HDI 群集，並從左側的選項中選擇**腳本操作**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="7f05c-139">提交一個腳本操作以在 HDInsight Spark 群集上部署 Apache Spark REPL 的 .NET。</span><span class="sxs-lookup"><span data-stu-id="7f05c-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="7f05c-140">套用下列設定：</span><span class="sxs-lookup"><span data-stu-id="7f05c-140">Use the following settings:</span></span>

   |<span data-ttu-id="7f05c-141">屬性</span><span class="sxs-lookup"><span data-stu-id="7f05c-141">Property</span></span>  |<span data-ttu-id="7f05c-142">描述</span><span class="sxs-lookup"><span data-stu-id="7f05c-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="7f05c-143">指令碼類型</span><span class="sxs-lookup"><span data-stu-id="7f05c-143">Script type</span></span> | <span data-ttu-id="7f05c-144">Custom</span><span class="sxs-lookup"><span data-stu-id="7f05c-144">Custom</span></span> |
   | <span data-ttu-id="7f05c-145">名稱</span><span class="sxs-lookup"><span data-stu-id="7f05c-145">Name</span></span> | <span data-ttu-id="7f05c-146">*安裝 .NET，用於 Apache Spark 互動式筆記本體驗*</span><span class="sxs-lookup"><span data-stu-id="7f05c-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="7f05c-147">Bash 指令碼 URI</span><span class="sxs-lookup"><span data-stu-id="7f05c-147">Bash script URI</span></span> | <span data-ttu-id="7f05c-148">您上傳 `install-interactive-notebook.sh` 的目標 URI。</span><span class="sxs-lookup"><span data-stu-id="7f05c-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="7f05c-149">節點類型</span><span class="sxs-lookup"><span data-stu-id="7f05c-149">Node type(s)</span></span>| <span data-ttu-id="7f05c-150">頭部和工人</span><span class="sxs-lookup"><span data-stu-id="7f05c-150">Head and Worker</span></span> |
   | <span data-ttu-id="7f05c-151">參數</span><span class="sxs-lookup"><span data-stu-id="7f05c-151">Parameters</span></span> | <span data-ttu-id="7f05c-152">阿帕奇火花版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="7f05c-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="7f05c-153">您可以檢查[.NET 的阿帕奇火花版本](https://github.com/dotnet/spark/releases)。</span><span class="sxs-lookup"><span data-stu-id="7f05c-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="7f05c-154">例如，如果要安裝 Sparkdotnet 版本 0.6.0，則它將是`0.6.0`。</span><span class="sxs-lookup"><span data-stu-id="7f05c-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="7f05c-155">當綠色核取記號顯示在腳本操作的狀態旁邊時，將移動到下一步。</span><span class="sxs-lookup"><span data-stu-id="7f05c-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="7f05c-156">啟動利維伺服器</span><span class="sxs-lookup"><span data-stu-id="7f05c-156">Start the Livy server</span></span>

<span data-ttu-id="7f05c-157">按照[停止利維伺服器](#stop-the-livy-server)部分**的說明開始（** 而不是**停止**）主機**hn0**和**hn1**的 Spark2 伺服器的 Livy。</span><span class="sxs-lookup"><span data-stu-id="7f05c-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="7f05c-158">設置 Spark 預設配置</span><span class="sxs-lookup"><span data-stu-id="7f05c-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="7f05c-159">從門戶中，選擇 **"概述**"，然後選擇**Ambari 主頁**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="7f05c-160">出現提示時，輸入叢集的叢集登入認證。</span><span class="sxs-lookup"><span data-stu-id="7f05c-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="7f05c-161">選擇**Spark2**和**CONFIGS**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="7f05c-162">然後，選擇**自訂 spark2 預設值**。</span><span class="sxs-lookup"><span data-stu-id="7f05c-162">Then, select **Custom spark2-defaults**.</span></span>

   ![設置配置](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="7f05c-164">選擇 **"添加屬性..."** 以添加 Spark 預設設置。</span><span class="sxs-lookup"><span data-stu-id="7f05c-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![新增屬性](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="7f05c-166">有三個單獨的屬性。</span><span class="sxs-lookup"><span data-stu-id="7f05c-166">There are three individual properties.</span></span> <span data-ttu-id="7f05c-167">在 Single 屬性添加模式下使用**TEXT**屬性類型一次添加一個。</span><span class="sxs-lookup"><span data-stu-id="7f05c-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="7f05c-168">檢查在任意鍵/值之前或之後沒有任何額外的空格。</span><span class="sxs-lookup"><span data-stu-id="7f05c-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="7f05c-169">**屬性 1**</span><span class="sxs-lookup"><span data-stu-id="7f05c-169">**Property 1**</span></span>
       * <span data-ttu-id="7f05c-170">關鍵：&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="7f05c-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="7f05c-171">值: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="7f05c-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="7f05c-172">**屬性 2**使用上一個腳本操作中包含的 Apache Spark 的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="7f05c-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="7f05c-173">關鍵：&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="7f05c-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="7f05c-174">值: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="7f05c-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="7f05c-175">**屬性 3**</span><span class="sxs-lookup"><span data-stu-id="7f05c-175">**Property 3**</span></span>
       * <span data-ttu-id="7f05c-176">關鍵：&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="7f05c-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="7f05c-177">值: `try`</span><span class="sxs-lookup"><span data-stu-id="7f05c-177">Value: `try`</span></span>

   <span data-ttu-id="7f05c-178">例如，下圖捕獲用於添加屬性 1 的設置：</span><span class="sxs-lookup"><span data-stu-id="7f05c-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![設置配置](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="7f05c-180">添加三個屬性後，選擇 **"保存**"。</span><span class="sxs-lookup"><span data-stu-id="7f05c-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="7f05c-181">如果您看到配置建議的警告螢幕，請選擇 **"執行"。**</span><span class="sxs-lookup"><span data-stu-id="7f05c-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="7f05c-182">重新開機受影響的元件。</span><span class="sxs-lookup"><span data-stu-id="7f05c-182">Restart affected components.</span></span>

   <span data-ttu-id="7f05c-183">添加新屬性後，需要重新開機受更改影響的元件。</span><span class="sxs-lookup"><span data-stu-id="7f05c-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="7f05c-184">在頂部，選擇**RESTART**，然後從下拉**清單中重新開機所有受影響的。**</span><span class="sxs-lookup"><span data-stu-id="7f05c-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![設置配置](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="7f05c-186">當提示時，選擇 **"確認全部"** 以繼續，然後按一下 **"確定**"以完成。</span><span class="sxs-lookup"><span data-stu-id="7f05c-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="7f05c-187">通過聚居筆記本提交作業</span><span class="sxs-lookup"><span data-stu-id="7f05c-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="7f05c-188">完成上述步驟後，您現在可以通過 Jupyter 筆記本提交用於 Apache Spark 作業的 .NET。</span><span class="sxs-lookup"><span data-stu-id="7f05c-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="7f05c-189">為 Apache Spark 筆記本創建新的 .NET。</span><span class="sxs-lookup"><span data-stu-id="7f05c-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="7f05c-190">從 Azure 門戶中的 HDI 群集啟動 Jupyter 筆記本。</span><span class="sxs-lookup"><span data-stu-id="7f05c-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![啟動朱皮特筆記本](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="7f05c-192">然後，選擇**新建** > **.NET Spark （C#）** 以創建筆記本。</span><span class="sxs-lookup"><span data-stu-id="7f05c-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="7f05c-194">使用 .NET 為 Apache Spark 提交作業。</span><span class="sxs-lookup"><span data-stu-id="7f05c-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="7f05c-195">使用以下程式碼片段創建資料幀：</span><span class="sxs-lookup"><span data-stu-id="7f05c-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![提交火花作業](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="7f05c-197">使用以下程式碼片段註冊使用者定義的函數 （UDF）， 並將 UDF 與 DataFrame 一起使用：</span><span class="sxs-lookup"><span data-stu-id="7f05c-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![提交火花作業](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="7f05c-199">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7f05c-199">Next steps</span></span>

* [<span data-ttu-id="7f05c-200">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="7f05c-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="7f05c-201">HDInsight 文檔</span><span class="sxs-lookup"><span data-stu-id="7f05c-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
