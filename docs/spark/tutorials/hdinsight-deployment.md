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
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>教程：將用於 Apache Spark 應用程式的 .NET 部署到 Azure HDInsight

本教程將介紹如何通過 Azure HDInsight 群集將 .NET 用於 Apache Spark 應用部署到雲中。 HDInsight 使在 Azure 中創建和配置 Spark 群集變得更加容易，因為 HDInsight 中的 Spark 群集與 Azure 存儲和 Azure 資料湖存儲相容。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 使用 Azure 存儲資源管理器訪問存儲帳戶。
> * 創建 Azure HDInsight 群集。
> * 發佈您的 .NET 用於 Apache Spark 應用。
> * 創建並運行 HDInsight 腳本操作。
> * 在 HDInsight 群集上運行 Apache Spark 應用的 .NET。

## <a name="prerequisites"></a>必要條件

在開始之前，執行以下任務：

* 如果沒有 Azure 訂閱，請創建[一個免費帳戶](https://azure.microsoft.com/free/)。
* 登錄到 Azure[門戶](https://portal.azure.com/)。
* 在[Windows、Linux](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)或[Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)[MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)電腦上安裝 Azure 存儲資源管理器。
* 完成[阿帕奇火花的 .NET - 在 10 分鐘教程中入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)。

## <a name="access-your-storage-accounts"></a>訪問存儲帳戶

1. 開啟 [Azure 儲存體總管]。

2. 選擇左側功能表上**的"添加帳戶**"，然後登錄到 Azure 帳戶。

    ![從存儲資源管理器登錄到 Azure 帳戶](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   登錄後，應查看您擁有的所有存儲帳戶以及已上載到存儲帳戶的任何資源。

## <a name="create-an-hdinsight-cluster"></a>建立 HDInsight 叢集

> [!IMPORTANT]
> 即使不使用 HDInsight 群集，也會每分鐘按比例計費。 請務必在使用完叢集後將其刪除。 有關詳細資訊，請參閱本教程的["清理資源](#clean-up-resources)"部分。

1. 訪問[Azure 門戶](https://portal.azure.com)。

2. 選擇 **= 創建資源**。 然後，從 **"分析"** 類別中選擇**HDInsight。**

    ![從 Azure 門戶創建 HDInsight 資源](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. 在 [基本]**** 下方，提供下列值：

    |屬性  |描述  |
    |---------|---------|
    |訂用帳戶  | 在下拉清單中，選擇一個活動 Azure 訂閱。 |
    |資源群組 | 指定您是要建立新的資源群組，還是使用現有資源群組。 資源群組是存放 Azure 方案相關資源的容器。 |
    |叢集名稱 | 提供 HDInsight Spark 叢集的名稱。|
    |Location   | 選取資源群組的位置。 此範本會使用這個位置，用於建立叢集以及預設叢集儲存體。 |
    |叢集類型| 選取 [spark]**** 作為叢集類型。|
    |叢集版本|選擇群集類型後，此欄位將自動填滿預設版本。 選擇 2.3 或 2.4 版本的 Spark。|
    |叢集登入使用者名稱| 輸入叢集登入使用者名稱。  預設名稱為 *admin*。 |
    |叢集登入密碼| 輸入任何登錄密碼。 |
    |安全殼層 (SSH) 使用者名稱| 輸入 SSH 使用者名稱。 根據預設，此帳戶會共用與「叢集登入使用者名稱」** 帳戶相同的密碼。 |

4. 選擇 **"下一步："存儲 >>** 以繼續訪問 **"存儲**"頁。 在 [儲存體]**** 下方，提供下列值：

    |屬性  |描述  |
    |---------|---------|
    |主要儲存體類型|使用預設值 [Azure 儲存體]****。|
    |選取方法|使用預設值 [從清單中選取]****。|
    |主要儲存體帳戶|選擇訂閱以及該訂閱中的一個活動存儲帳戶。|
    |容器|此容器是存儲帳戶中的特定 Blob 容器，群集在其中查找在雲中運行應用的檔。 您可以給它任何可用的名稱。|

5. 在 [檢閱 + 建立]**** 底下，選取 [建立]****。 大約需要 20 分鐘的時間來建立叢集。 必須先創建群集，然後才能繼續執行下一步。

## <a name="publish-your-app"></a>發佈您的應用程式

接下來，發佈在 .NET 中創建的[mySparkApp，用於 Apache Spark - 在 10 分鐘內入門](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教程，該教程允許 Spark 群集訪問運行應用所需的所有檔。 *mySparkApp*

1. 運行以下命令以發佈*mySparkApp*：

   **在 Windows 上：**

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **在 Linux 上：**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. 執行以下任務來壓縮已發佈的應用檔，以便可以輕鬆地將它們上載到 HDInsight 群集。

   **在 Windows 上：**

   導航到*mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64*。 然後，按右鍵 **"發佈**"資料夾，然後選擇"**發送到>壓縮（壓縮）資料夾**。 為新資料夾**publish.zip 命名**。

   **在 Linux 上，運行以下命令：**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>將檔上載到 Azure

接下來，使用 Azure 存儲資源管理器將以下五個檔上載到為群集存儲選擇的 Blob 容器：

* 微軟.Spark.Worker
* install-worker.sh
* 發佈.zip
* 微軟火花-2.3.x-0.3.0.jar
* 輸入.txt.

1. 打開 Azure 存儲資源管理器，並從左側功能表導航到存儲帳戶。 向下切入到存儲帳戶中的 Blob**容器**下的群集 Blob 容器。

2. *Microsoft.Spark.Worker*説明 Apache Spark 執行你的應用，例如您可能編寫的任何使用者定義的函數 （UF）。 下載[微軟.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)。 然後，選擇 **"在**Azure 存儲資源管理器中上載"以上載輔助角色。

   ![將檔上載到 Azure 存儲資源管理器](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *install-worker.sh*是一個腳本，允許您將 Apache Spark 相關檔的 .NET 複製到群集的節點中。

   創建名為**install-worker.sh**本地電腦的新檔，並粘貼位於 GitHub 上的[install-worker.sh內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。 然後，將*install-worker.sh*上載到 blob 容器。

4. 群集需要包含應用已發佈的檔的 publish.ZIP 檔案。 導航到已發佈的資料夾 **，mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64**，並找到**發佈.zip**. 然後上載*Publish.zip*到 blob 容器。

5. 群集需要打包到 jar 檔中的應用程式代碼。 導航到您已發佈的資料夾 **，mySparkApp/bin/發佈/netcoreapp3.0/ubuntu.16.04-x64**，並找到**微軟-spark-2.3.x-0.3.0.jar**。 然後，將 jar 檔上載到 blob 容器。

   可能有多個 .jar 檔（對於 Spark 的版本 2.3.x 和 2.4.x）。 您需要選擇與群集創建期間選擇的 Spark 版本相匹配的 .jar 檔。 例如，如果在群集創建期間選擇 Spark 2.3.2，請選擇*Microsoft-spark-2.3.x-0.3.0.jar。*

6. 群集需要輸入到應用。 導航到您的**mySparkApp**目錄並找到**輸入.txt**。 將輸入檔上載到 blob 容器中的**使用者/sshuser**目錄。 您將通過 ssh 連接到群集，此資料夾是群集查找其輸入的位置。 *input.txt*檔是唯一上載到特定目錄的檔。

## <a name="run-the-hdinsight-script-action"></a>運行 HDInsight 腳本操作

群集運行並將檔上載到 Azure 後，在群集上運行**install-worker.sh**腳本。

1. 導航到 Azure 門戶中的 HDInsight Spark 群集，然後選擇**腳本操作**。

2. 選擇 **= 提交新**值並提供以下值：

   |屬性  |描述  |
   |---------|---------|
   | 指令碼類型 |Custom|
   | 名稱 | 安裝輔助角色|
   | Bash 指令碼 URI |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> 要確認此 URI，請按右鍵 Azure 存儲資源管理器中的install-worker.sh並選擇屬性。 |
   | 節點類型| 背景工作|
   | 參數 | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/本地/箱

3. 選擇 **"創建**"以提交腳本。

## <a name="run-your-app"></a>執行您的應用程式

1. 導航到 Azure 門戶中的 HDInsight Spark 群集，然後選擇**SSH + 群集登錄**。

2. 複製 ssh 登錄資訊並將登錄粘貼到終端中。 使用在群集創建期間設置的密碼登錄到群集。 您應該會看到歡迎您訪問 Ubuntu 和 Spark 的消息。

3. 使用**火花提交**命令在 HDInsight 群集上運行應用。 請記住，在示例腳本中用 blob 容器和存儲帳戶的實際名稱替換**我的容器**和**我的存儲帳戶**。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   應用運行時，您會看到從已啟動的本地運行中寫入主控台的相同字計數表。 恭喜您，您已經運行了第一個 .NET 在雲中的 Apache Spark 應用程式！

## <a name="clean-up-resources"></a>清除資源

HDInsight 將資料保存在 Azure 存儲中，因此您可以安全地刪除群集時未使用。 您也需支付 HDInsight 叢集的費用 (即使未使用)。 由於叢集費用是儲存體費用的許多倍，所以刪除未使用的叢集符合經濟效益。

您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]****。 刪除資源群組時，會同時刪除 HDInsight Spark 叢集及預設儲存體帳戶。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。 若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。

> [!div class="nextstepaction"]
> [Azure HDInsight 文檔](https://docs.microsoft.com/azure/hdinsight/)
