---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3b00823034cbcb271cb7e169df40122f1144462a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895721"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>教學課程：將適用于 Apache Spark 應用程式的 .NET 部署至 Databricks

本教學課程將教您如何透過 Azure Databricks （以 Apache Spark 為基礎的分析平臺），將您的應用程式部署到雲端，其中包含單鍵設定、簡化的工作流程，以及啟用共同作業的互動式工作區。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 建立 Azure Databricks 工作區。
> - 發行您的 .NET for Apache Spark 應用程式。
> - 建立 Spark 作業和 Spark 叢集。
> - 在 Spark 叢集上執行您的應用程式。

## <a name="prerequisites"></a>Prerequisites

開始之前，請執行下列工作：

* 如果您沒有 Azure 帳戶，請建立[免費帳戶](https://azure.microsoft.com/free/dotnet/)。
* 登入 [Azure 入口網站](https://portal.azure.com/)。
* 完成[Apache Spark 的 .net-在10分鐘內開始](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)使用教學課程。

## <a name="create-an-azure-databricks-workspace"></a>建立 Azure Databricks 工作區

> [!Note]
> 本教學課程不適用 **Azure 免費試用版的訂用帳戶**。
> 如果您有免費帳戶，請移至您的設定檔，並將訂用帳戶變更為**隨用隨付**。 如需詳細資訊，請參閱 [Azure 免費帳戶](https://azure.microsoft.com/free/dotnet/)。 然後，為您所在區域的 vCPU [移除消費限制](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)並[要求增加配額](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request)。 當您建立 Azure Databricks 工作區時，您可以選取 [試用版 (進階 - 14 天的免費 DBU)]  定價層，讓工作區可免費存取進階 Azure Databricks DBU 14 天。

在本節中，您會使用 Azure 入口網站建立 Azure Databricks 工作區。

1. 在 Azure 入口網站中，選取 [建立資源]   > [分析]   > [Azure Databricks]  。

   ![在 Azure 入口網站中建立 Azure Databricks 資源](./media/databricks-deployment/create-databricks-resource.png)

2. 在 [Azure Databricks 服務]**** 底下，提供值以建立 Databricks 工作區。

    |屬性  |描述  |
    |---------|---------|
    |**工作區名稱**     | 提供您 Databricks 工作區的名稱。        |
    |**訂用帳戶**     | 從下拉式清單中選取您的 Azure 訂用帳戶。        |
    |**資源群組**     | 指定您是要建立新的資源群組，還是使用現有資源群組。 資源群組是存放 Azure 方案相關資源的容器。 如需詳細資訊，請參閱 [Azure 資源群組概觀](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)。 |
    |**位置**     | 選取您的慣用區域。 如需可用區域的詳細資訊，請參閱[依區域提供的 Azure 服務](https://azure.microsoft.com/regions/services/)。        |
    |定價層      |  選擇 [標準]****、[進階]**** 或 [試用]****。 如需這些定價層的詳細資訊，請參閱 [Databricks 定價頁面](https://azure.microsoft.com/pricing/details/databricks/)。       |
    |**虛擬網路**     |   否       |

3. 選取 [建立]  。 工作區建立需要幾分鐘的時間。 在工作區建立期間，您可以在 [通知]**** 中檢視部署狀態。

## <a name="install-azure-databricks-tools"></a>安裝 Azure Databricks 工具

您可以使用**DATABRICKS CLI**來連線到 Azure Databricks 叢集，並從本機電腦將檔案上傳到其中。 Databricks 叢集會透過 DBFS （Databricks 檔案系統）存取檔案。

1. Databricks CLI 需要 Python 3.6 或更新版本。 如果您已經安裝 Python，可以略過此步驟。

   **若為 Windows：**

   [下載適用于 Windows 的 Python](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   若**為 Linux：** Python 已預先安裝于大部分的 Linux 發行版本上。 執行下列命令，以查看您已安裝的版本：

   ```bash
   python3 --version
   ```

2. 使用 pip 安裝 Databricks CLI。 根據預設，Python 3.4 和更新版本包含 pip。 使用適用于 Python 3 的 pip3。 執行以下命令：

   ```bash
   pip3 install databricks-cli
   ```

3. 安裝 Databricks CLI 之後，請開啟新的命令提示字元，然後執行命令`databricks`。 如果您收到「 **databricks」無法辨識為內部或外部命令錯誤**，請確定您已開啟新的命令提示字元。

## <a name="set-up-azure-databricks"></a>設定 Azure Databricks

既然您已安裝 Databricks CLI，您必須設定驗證詳細資料。

1. 執行 Databricks CLI 命令`databricks configure --token`。

2. 執行 [設定] 命令之後，系統會提示您輸入主機。 您的主機 URL 使用下列格式： **HTTPs://< \location>. azuredatabricks.net**。 例如，如果您在 Azure Databricks 服務建立期間選取了 [ **eastus2** ]，則**https://eastus2.azuredatabricks.net**主機會是。

3. 進入主機之後，系統會提示您輸入權杖。 在 [Azure 入口網站中，選取 [**啟動工作區**] 以啟動您的 Azure Databricks 工作區。

   ![啟動 Azure Databricks 工作區](./media/databricks-deployment/launch-databricks-workspace.png)

4. 在工作區的 [首頁] 頁面上，選取 [**使用者設定**]。

   ![Azure Databricks 工作區中的使用者設定](./media/databricks-deployment/databricks-user-settings.png)

5. 在 [使用者設定] 頁面上，您可以產生新的權杖。 複製產生的權杖，並將它貼回命令提示字元。

   ![在 Azure Databricks 工作區中產生新的存取權杖](./media/databricks-deployment/generate-token.png)

您現在應該能夠存取您建立的任何 Azure Databricks 叢集，並將檔案上傳到 DBFS。

## <a name="download-worker-dependencies"></a>下載背景工作相依性

1. Apache Spark 可協助執行您的應用程式，例如您可能已撰寫的任何使用者定義函數（Udf）。 下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)。

2. *Install-worker.sh*是一個腳本，可讓您將 Apache Spark 相依檔案的 .net 複製到叢集的節點中。

   在您的本機電腦上建立名為**install-worker.sh**的新檔案，並貼上位於 GitHub 的[install-worker.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。

3. *Db-init.sh*是將相依性安裝在您的 Databricks Spark 叢集上的腳本。

   在您的本機電腦上建立名為**db-init.sh**的新檔案，並貼上位於 GitHub 的[db-init.sh 內容](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)。

   在您剛才建立的檔案中，將`DOTNET_SPARK_RELEASE`變數設定`https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`為。 保留*db-init.sh*檔案的其餘部分。

> [!Note]
> 如果您使用的是 Windows，請確認您的*install-worker.sh*和*db-init.sh*腳本中的行尾結束符號為 Unix 樣式（LF）。 您可以透過 [記事本 + +] 和 [Atom] 之類的文字編輯器來變更行尾結束符號。

## <a name="publish-your-app"></a>發佈您的應用程式

接下來，您會發佈在 .Net 中建立[Apache Spark-開始使用10分鐘](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)的教學課程中的*mySparkApp* ，以確保您的 Spark 叢集能夠存取執行應用程式所需的所有檔案。

1. 執行下列命令以發佈*mySparkApp*：

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. 執行下列工作以壓縮已發佈的應用程式檔，讓您可以輕鬆地將它們上傳到您的 Databricks Spark 叢集。

   **在 Windows 上：**

   流覽至 mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64。 然後，在 [**發行**資料夾] 上按一下滑鼠右鍵，然後選取 **[傳送至 > 壓縮的（zipped）資料夾**]。 將新資料夾命名為**publish .zip**。

   **在 Linux 上，執行下列命令：**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>上傳檔案

在本節中，您會將數個檔案上傳至 DBFS，讓您的叢集具備在雲端中執行應用程式所需的所有專案。 每次您將檔案上傳到 DBFS 時，請確定您位於電腦上該檔案所在的目錄中。

1. 執行下列命令，將*db-init.sh*、 *install-worker.sh*和 DBFS 上傳*至*：

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. 執行下列命令，上傳您的叢集執行應用程式所需的其餘檔案：壓縮的 publish 資料夾、 *input .txt*和*microsoft-spark-2.4. x-0.3.0 .jar*。

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a>建立作業

您的應用程式會透過執行**spark 提交**的作業在 Azure Databricks 上執行，這是您用來針對 Apache Spark 作業執行 .net 的命令。

1. 在您的 Azure Databricks 工作區中，選取 [**作業**] 圖示，然後選取 [ **+ 建立作業**]。

   ![建立 Azure Databricks 作業](./media/databricks-deployment/create-job.png)

2. 選擇您的作業標題，然後選取 [**設定 spark-提交**]。

   ![設定 spark-提交 Databricks 作業](./media/databricks-deployment/configure-spark-submit.png)

3. 在作業設定中貼上下列參數。 然後選取 [**確認**]。

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>建立叢集

1. 流覽至您的作業，然後選取 [**編輯**] 來設定作業的叢集。

2. 將您的叢集設定為**Spark 2.4.1**。 然後，選取 [ **Advanced Options** > **Init Scripts**]。 將 [初始化腳本路徑`dbfs:/spark-dotnet/db-init.sh`] 設定為。

   ![在 Azure Databricks 中設定 spark 叢集](./media/databricks-deployment/cluster-config.png)

3. 選取 [**確認**] 以確認您的叢集設定。

## <a name="run-your-app"></a>執行您的應用程式

1. 流覽至您的作業，然後選取 [**立即執行**]，在新設定的 Spark 叢集上執行您的作業。

2. 建立作業的叢集需要幾分鐘的時間。 建立之後，將會提交您的作業，而且您可以查看輸出。

3. 從左側功能表**中選取 [** 叢集]，然後從 [名稱] 和 [執行您的作業]。

4. 選取 [**驅動程式記錄**] 以查看作業的輸出。 當您的應用程式完成執行時，您會看到寫入標準輸出主控台的「快速入門」本機執行中的相同字數統計表。

   ![Azure Databricks 作業輸出資料表](./media/databricks-deployment/table-output.png)

   恭喜，您已在雲端中執行 Apache Spark 應用程式的第一個 .NET！

## <a name="clean-up-resources"></a>清除資源

如果您不再需要 Databricks 工作區，您可以在 Azure 入口網站中刪除您的 Azure Databricks 資源。 您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]  。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。 若要深入了解 Databricks，請繼續前往 Azure Databricks 文件。

> [!div class="nextstepaction"]
> [Azure Databricks 文件](https://docs.microsoft.com/azure/azure-databricks/)
