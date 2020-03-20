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
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>教程：將用於 Apache Spark 應用程式的 .NET 部署到資料磚塊

本教程教您如何通過 Azure 資料磚塊（基於 Apache Spark 的分析平臺）將應用部署到雲中，該平臺具有一鍵式設置、簡化的工作流和互動式工作區，可實現協作。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> - 建立 Azure Databricks 工作區。
> - 發佈您的 .NET 用於 Apache Spark 應用。
> - 創建 Spark 作業和 Spark 群集。
> - 在 Spark 群集上運行應用。

## <a name="prerequisites"></a>必要條件

在開始之前，執行以下任務：

* 如果沒有 Azure 帳戶，請創建[一個免費帳戶](https://azure.microsoft.com/free/)。
* 登錄到 Azure[門戶](https://portal.azure.com/)。
* 完成[阿帕奇火花的 .NET - 在 10 分鐘教程中入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)。

## <a name="create-an-azure-databricks-workspace"></a>建立 Azure Databricks 工作區

> [!Note]
> 本教學課程不適用 **Azure 免費試用版的訂用帳戶**。
> 如果您有免費帳戶，請移至您的設定檔，並將訂用帳戶變更為**隨用隨付**。 如需詳細資訊，請參閱 [Azure 免費帳戶](https://azure.microsoft.com/free/)。 然後，為您所在區域的 vCPU [移除消費限制](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)並[要求增加配額](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request)。 當您建立 Azure Databricks 工作區時，您可以選取 [試用版 (進階 - 14 天的免費 DBU)]**** 定價層，讓工作區可免費存取進階 Azure Databricks DBU 14 天。

在本節中，您會使用 Azure 入口網站建立 Azure Databricks 工作區。

1. 在 Azure 門戶中，選擇 **"創建資源** > **分析** > **Azure 資料塊**"。

   ![在 Azure 門戶中創建 Azure 資料磚塊資源](./media/databricks-deployment/create-databricks-resource.png)

2. 在 [Azure Databricks 服務]**** 底下，提供值以建立 Databricks 工作區。

    |屬性  |描述  |
    |---------|---------|
    |**工作區名稱**     | 提供您 Databricks 工作區的名稱。        |
    |**訂閱**     | 從下拉式清單中選取您的 Azure 訂用帳戶。        |
    |**資源組**     | 指定您是要建立新的資源群組，還是使用現有資源群組。 資源群組是存放 Azure 方案相關資源的容器。 如需詳細資訊，請參閱 [Azure 資源群組概觀](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)。 |
    |**位置**     | 選取您的慣用區域。 有關可用區域的資訊，請參閱[按區域提供的 Azure 服務](https://azure.microsoft.com/regions/services/)。        |
    |**定價層**     |  選擇 [標準]****、[進階]**** 或 [試用]****。 如需這些定價層的詳細資訊，請參閱 [Databricks 定價頁面](https://azure.microsoft.com/pricing/details/databricks/)。       |
    |**虛擬網路**     |   否       |

3. 選取 [建立]****。 工作區建立需要幾分鐘的時間。 在工作區建立期間，您可以在 [通知]**** 中檢視部署狀態。

## <a name="install-azure-databricks-tools"></a>安裝 Azure 資料磚塊工具

可以使用**DataBRICKS CLI**連接到 Azure 資料磚塊群集，並從本地電腦將檔上載到它們。 資料磚群集通過 DBFS（資料磚檔案系統）訪問檔。

1. 資料磚 CLI 需要 Python 3.6 或以上。 如果您已經安裝了 Python，則可以跳過此步驟。

   **對於視窗：**

   [下載適用于 Windows 的 Python](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **對於 Linux：** Python 預先安裝在大多數 Linux 發行版本上。 運行以下命令以查看已安裝的版本：

   ```bash
   python3 --version
   ```

2. 使用點子安裝資料磚 CLI。 預設情況下，Python 3.4 及更高版本包括點。 對 Python 3 使用 pip3。 執行以下命令：

   ```bash
   pip3 install databricks-cli
   ```

3. 安裝 DataBRICKS CLI 後，打開新的命令提示符並運行命令`databricks`。 如果收到 **"資料磚"未識別為內部或外部命令錯誤**，請確保打開新的命令提示符。

## <a name="set-up-azure-databricks"></a>設置 Azure 資料塊

現在，您已經安裝了 DataBRICKS CLI，您需要設置身份驗證詳細資訊。

1. 運行資料磚 CLI`databricks configure --token`命令 。

2. 回合組態命令後，系統將提示您輸入主機。 您的主機 URL 使用格式： **HTTPs：//<_location>.azuredatabricks.net**. 例如，如果在 Azure 資料磚塊服務創建期間選擇了**Eastus2，** 則主機將是**https://eastus2.azuredatabricks.net**。

3. 輸入主機後，系統會提示您輸入權杖。 在 Azure 門戶中，選擇 **"啟動工作區"** 以啟動 Azure 資料塊工作區。

   ![啟動 Azure 資料塊工作區](./media/databricks-deployment/launch-databricks-workspace.png)

4. 在工作區的主頁上，選擇 **"使用者設置**"。

   ![Azure 資料磚塊工作區中的使用者設置](./media/databricks-deployment/databricks-user-settings.png)

5. 在"使用者設置"頁上，可以生成新權杖。 複製生成的權杖並將其粘貼回命令提示符。

   ![在 Azure 資料塊工作區中生成新的訪問權杖](./media/databricks-deployment/generate-token.png)

現在，您應該能夠訪問創建的任何 Azure 資料磚塊群集，並將檔上載到 DBFS。

## <a name="download-worker-dependencies"></a>下載輔助角色依賴項

1. Microsoft.Spark.Worker 説明 Apache Spark 執行你的應用，例如您可能編寫的任何使用者定義的函數 （UF）。 下載[微軟.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)。

2. *install-worker.sh*是一個腳本，允許您將 Apache Spark 相關檔的 .NET 複製到群集的節點中。

   在本地電腦上創建名為**install-worker.sh**的新檔，並粘貼位於 GitHub 上的[install-worker.sh內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。

3. *db-init.sh*是一個腳本，用於將依賴項安裝到 Databricks Spark 群集上。

   在本地電腦上創建名為**db-init.sh**的新檔，並粘貼位於 GitHub 上的[db-init.sh內容](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)。

   在剛剛創建的檔中，將`DOTNET_SPARK_RELEASE`變數設置為`https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`。 保留*db-init.sh*檔的其餘部分。

> [!Note]
> 如果使用 Windows，請驗證*install-worker.sh*和*db-init.sh*腳本中的行尾是否為 Unix 樣式 （LF）。 您可以通過文字編輯器（如記事本* 和 Atom）更改行尾。

## <a name="publish-your-app"></a>發佈您的應用程式

接下來，發佈在 .NET 中創建的[mySparkApp，用於 Apache Spark - 在 10 分鐘內入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程，以確保 Spark 群集有權訪問運行應用所需的所有檔。 *mySparkApp*

1. 運行以下命令以發佈*mySparkApp*：

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. 執行以下任務來壓縮已發佈的應用檔，以便可以輕鬆地將它們上載到 Databricks Spark 群集。

   **在 Windows 上：**

   導航到 mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64。 然後，按右鍵 **"發佈**"資料夾，然後選擇"**發送到>壓縮（壓縮）資料夾**。 為新資料夾**publish.zip 命名**。

   **在 Linux 上，運行以下命令：**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>上傳檔案

在本節中，您將多個檔上載到 DBFS，以便群集擁有在雲中運行應用所需的一切。 每次將檔上載到 DBFS 時，請確保位於該檔位於電腦上的目錄中。

1. 運行以下命令以上載*db-init.sh、install-worker.sh*和*Microsoft.Spark.Worker*到 DBFS： *install-worker.sh*

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. 運行以下命令以上載群集運行應用所需的其餘檔：壓縮的發佈資料夾 *、input.txt*和*Microsoft-spark-2.4.x-0.3.0.jar*。

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>建立作業

你的應用通過運行**spark-提交**的作業在 Azure Databricks 上運行 ，這是用於為 Apache Spark 作業運行 .NET 的命令。

1. 在 Azure 資料塊工作區中，選擇**作業**圖示，然後 **+ 創建作業**。

   ![創建 Azure 資料磚塊作業](./media/databricks-deployment/create-job.png)

2. 為作業選擇標題，然後選擇 **"配置火花提交**"。

   ![為數據磚塊作業配置火花提交](./media/databricks-deployment/configure-spark-submit.png)

3. 在作業配置中粘貼以下參數。 然後，選擇 **"確認**"。

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>建立叢集

1. 導航到作業並選擇 **"編輯"** 以配置作業的群集。

2. 將群集設置為**Spark 2.4.1**。 然後，選擇**高級選項** > **Init 腳本**。 將 Init 腳本`dbfs:/spark-dotnet/db-init.sh`路徑設置為 。

   ![在 Azure 資料塊中配置火花群集](./media/databricks-deployment/cluster-config.png)

3. 選擇 **"確認**"以確認群集設置。

## <a name="run-your-app"></a>執行您的應用程式

1. 導航到作業，然後選擇 **"立即運行"** 以在新配置的 Spark 群集上運行作業。

2. 創建作業的群集需要幾分鐘時間。 創建作業後，將提交作業，您可以查看輸出。

3. 從左側功能表中選擇 **"群集**"，然後選擇作業的名稱和運行。

4. 選擇**驅動程式日誌**以查看作業的輸出。 應用完成執行後，您將看到從已啟動的本地運行中寫入標準輸出主控台的相同字計數表。

   ![Azure 資料磚塊作業輸出表](./media/databricks-deployment/table-output.png)

   恭喜您，您已經運行了第一個 .NET 在雲中的 Apache Spark 應用程式！

## <a name="clean-up-resources"></a>清除資源

如果不再需要 DataBRICKS 工作區，則可以在 Azure 門戶中刪除 Azure 資料磚塊資源。 您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]****。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。 若要深入了解 Databricks，請繼續前往 Azure Databricks 文件。

> [!div class="nextstepaction"]
> [Azure Databricks 文件](https://docs.microsoft.com/azure/azure-databricks/)
