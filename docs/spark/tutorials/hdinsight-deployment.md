---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 HDInsight。
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c745231f76142c11002ac6663906c8c44c69cdae
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223351"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>教學課程：將 Apache Spark 應用程式的 .NET 部署至 Azure HDInsight

本教學課程會教您如何透過 Azure HDInsight 叢集，將 Apache Spark 應用程式的 .NET 部署至雲端。 HDInsight 可讓您更輕鬆地在 Azure 中建立和設定 Spark 叢集，因為 HDInsight 中的 Spark 叢集與 Azure 儲存體和 Azure Data Lake Storage 相容。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 使用 Azure 儲存體總管存取您的儲存體帳戶。
> * 建立 Azure HDInsight 叢集。
> * 發行您的 .NET 以 Apache Spark 應用程式。
> * 建立並執行 HDInsight 腳本動作。
> * 在 HDInsight 叢集上執行 Apache Spark 應用程式的 .NET。

## <a name="prerequisites"></a>Prerequisites

開始之前，請執行下列工作：

* 如果您沒有 Azure 訂用帳戶，請建立[免費帳戶](https://azure.microsoft.com/free/dotnet/)。
* 登入 [Azure 入口網站](https://portal.azure.com/)。
* 在您的 [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)、 [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)或 [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) 電腦上安裝 Azure 儲存體總管。
* [在10分鐘](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)的教學課程中完成 Apache Spark 開始的 .net。

## <a name="access-your-storage-accounts"></a>存取您的儲存體帳戶

1. 開啟 [Azure 儲存體總管]。

2. 在左側功能表上選取 [ **新增帳戶** ]，然後登入您的 Azure 帳戶。

    ![從儲存體總管登入 Azure 帳戶](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   登入之後，您應該會看到您擁有的所有儲存體帳戶，以及您已上傳至儲存體帳戶的任何資源。

## <a name="create-an-hdinsight-cluster"></a>建立 HDInsight 叢集

> [!IMPORTANT]
> HDInsight 叢集的計費是按分鐘計費，即使您未使用它們也是一樣。 請務必在使用完叢集後將其刪除。 如需詳細資訊，請參閱本教學課程的「 [清除資源](#clean-up-resources) 」一節。

1. 造訪 [Azure 入口網站](https://portal.azure.com)。

2. 選取 [+ 建立資源]。 然後，從 [**分析**] 類別選取 [ **HDInsight** ]。

    ![從 Azure 入口網站建立 HDInsight 資源](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. 在 [ **基本**] 底下，提供下列值：

    |屬性  |描述  |
    |---------|---------|
    |訂用帳戶  | 從下拉式清單中，選擇其中一個作用中的 Azure 訂用帳戶。 |
    |資源群組 | 指定您是要建立新的資源群組，還是使用現有資源群組。 資源群組是存放 Azure 方案相關資源的容器。 |
    |叢集名稱 | 提供 HDInsight Spark 叢集的名稱。|
    |位置   | 選取資源群組的位置。 此範本會使用這個位置，用於建立叢集以及預設叢集儲存體。 |
    |叢集類型| 選取 [ **Spark** ] 作為叢集類型。|
    |叢集版本|一旦選取叢集類型，此欄位就會以預設版本自動填入。 選取 [2.3] 或 [2.4] 版本的 Spark。|
    |叢集登入使用者名稱| 輸入叢集登入使用者名稱。  預設名稱為 *admin*。 |
    |叢集登入密碼| 輸入任何登入密碼。 |
    |安全殼層 (SSH) 使用者名稱| 輸入 SSH 使用者名稱。 根據預設，此帳戶會共用與「叢集登入使用者名稱」  帳戶相同的密碼。 |

4. 完成時，選取 [下一步:  儲存體>>] 繼續前往 [儲存體]  頁面。 在 [儲存體]  下方，提供下列值：

    |屬性  |描述  |
    |---------|---------|
    |主要儲存體類型|使用預設值 [Azure 儲存體]  。|
    |選取方法|使用預設值 [從清單中選取]  。|
    |主要儲存體帳戶|選擇您的訂用帳戶，以及該訂用帳戶內的其中一個作用中儲存體帳戶。|
    |容器|此容器是您儲存體帳戶中的特定 blob 容器，您的叢集會在該容器中尋找檔案，以便在雲端中執行您的應用程式。 您可以為其提供任何可用的名稱。|

5. 在 [檢閱 + 建立]  底下，選取 [建立]  。 大約需要 20 分鐘的時間來建立叢集。 您必須先建立叢集，才能繼續下一個步驟。

## <a name="publish-your-app"></a>發佈您的應用程式

接下來，您會在10分鐘的教學課程中發佈在 .Net 中建立的 *mySparkApp* ，以 [開始 Apache Spark 供](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) 您的 Spark 叢集存取執行應用程式所需的所有檔案。

1. 執行下列命令以發佈 *mySparkApp*：

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

2. 請執行下列工作來壓縮已發佈的應用程式檔，讓您可以輕鬆地將它們上傳至您的 HDInsight 叢集。 壓縮 [發佈] 資料夾的內容，例如步驟1所建立的 *publish.zip* 。 所有元件都應該在 ZIP 檔案的第一層，而且不應該有中繼資料夾層。 這表示當您將 *publish.zip*解壓縮時，所有元件都會解壓縮至您目前的工作目錄中。

   **在 Windows 上：**

   使用類似 7-Zip 或 WinZip 的解壓縮程式，將檔案解壓縮到 bin 目錄中，並包含所有已發佈的二進位檔。

   **在 Linux 上，執行下列命令：**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>將檔案上傳至 Azure

接下來，您會使用 Azure 儲存體總管將下列五個檔案上傳至您為叢集儲存體選擇的 blob 容器：

* Microsoft. 背景工作
* install-worker.sh
* publish.zip
* microsoft-spark-2.3. x-0.3.0 .jar
* input.txt。

1. 開啟 Azure 儲存體總管，然後從左側功能表流覽至您的儲存體帳戶。 在儲存體帳戶中的 **Blob 容器** 下向下切入至您叢集的 blob 容器。

2. Apache Spark*可協助*執行您的應用程式，例如您可能已撰寫 (udf) 的任何使用者定義函數。 下載 [Microsoft. 背景工作角色](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)。 然後，選取 Azure 儲存體總管 **上傳** 以上傳背景工作角色。

   ![將檔案上傳至 Azure 儲存體總管](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *Install-worker.sh*是可讓您將 Apache Spark 相依檔案的 .net 複製到叢集節點的腳本。

   在本機電腦上建立名為 **install-worker.sh** 的新檔案，並貼上位於 GitHub 上的 [install-worker.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) 。 然後，將 *install-worker.sh* 上傳至 blob 容器。

4. 您的叢集需要 publish.zip 檔案，其中包含應用程式的已發佈檔案。 流覽至您已發佈的資料夾 **mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64**，然後找出 **publish.zip**。 然後將 *publish.zip* 上傳至 blob 容器。

5. 您的叢集需要封裝至 jar 檔案的應用程式程式碼。 流覽至您已發佈的資料夾 **mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64**，然後找出 **microsoft-spark-2.3. x-0.3.0 .jar**。 然後，將 jar 檔案上傳至 blob 容器。

   針對 2.x. x 和 2.4. x 版的 Spark) ，可能會有多個 .jar 檔案 (。 您必須選擇符合您在叢集建立期間所選擇之 Spark 版本的 .jar 檔案。 例如，如果您在叢集建立期間選擇 Spark 2.3.2，請選擇 *microsoft-spark-2.3. x-0.3.0 .jar* 。

6. 您的叢集需要輸入至您的應用程式。 流覽至您的 **mySparkApp** 目錄，並找出 **input.txt**。 將您的輸入檔上傳至 blob 容器中的 **使用者/sshuser** 目錄。 您將透過 ssh 連線到您的叢集，而此資料夾是您的叢集尋找其輸入的位置。 *input.txt*檔案是上傳至特定目錄的唯一檔案。

## <a name="run-the-hdinsight-script-action"></a>執行 HDInsight 腳本動作

當您的叢集正在執行，且您已將檔案上傳至 Azure 之後，您會在叢集上執行 **install-worker.sh** 腳本。

1. 在 Azure 入口網站中流覽至您的 HDInsight Spark 叢集，然後選取 [ **腳本動作**]。

2. 選取 [ **+ 提交新** 的] 並提供下列值：

   |屬性  |描述  |
   |---------|---------|
   | 指令碼類型 |自訂|
   | 名稱 | 安裝背景工作|
   | Bash 指令碼 URI |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> 若要確認此 URI，請在 Azure 儲存體總管中的 install-worker.sh 上按一下滑鼠右鍵，然後選取 [屬性]。 |
   | 節點類型| 背景工作|
   | 參數 | azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. 選取 [ **建立** ] 來提交您的腳本。

## <a name="run-your-app"></a>執行應用程式

1. 在 Azure 入口網站中流覽至您的 HDInsight Spark 叢集，然後選取 **[SSH + 叢集登**入]。

2. 複製 ssh 登入資訊，並將登入貼到終端機。 使用您在叢集建立期間設定的密碼來登入您的叢集。 您應該會看到歡迎您前往 Ubuntu 和 Spark 的訊息。

3. 使用 **spark 提交** 命令，在您的 HDInsight 叢集上執行您的應用程式。 請記得將範例腳本中的 **mycontainer** 和 **mystorageaccount** 取代為 blob 容器和儲存體帳戶的實際名稱。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   當您的應用程式執行時，您會看到來自寫入至主控台的「開始使用」本機執行的相同「字數統計」表格。 恭喜，您已在雲端中執行 Apache Spark 應用程式的第一個 .NET！

## <a name="clean-up-resources"></a>清除資源

HDInsight 會將您的資料儲存在 Azure 儲存體中，因此您可以在未使用的情況下安全地刪除叢集。 您也需支付 HDInsight 叢集的費用 (即使未使用)。 由於叢集費用是儲存體費用的許多倍，所以刪除未使用的叢集符合經濟效益。

您也可以選取資源群組名稱來開啟資源群組頁面，然後選取 [刪除資源群組]。 刪除資源群組時，會同時刪除 HDInsight Spark 叢集及預設儲存體帳戶。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。 若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。

> [!div class="nextstepaction"]
> [Azure HDInsight 文件](/azure/hdinsight/)
