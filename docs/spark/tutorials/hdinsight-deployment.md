---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 HDInsight。
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 76a150879324640352aa36f753ec3d6e7342bcaf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860774"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>教學課程：將適用于 Apache Spark 應用程式的 .NET 部署至 Azure HDInsight

本教學課程會教您如何透過 Azure HDInsight 叢集，將 Apache Spark 應用程式的 .NET 部署至雲端。 HDInsight 可讓您更輕鬆地在 Azure 中建立和設定 Spark 叢集，因為 HDInsight 中的 Spark 叢集與 Azure 儲存體和 Azure Data Lake Storage 相容。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 使用 Azure 儲存體總管存取儲存體帳戶。
> * 建立 Azure HDInsight 叢集。
> * 發行您的 .NET for Apache Spark 應用程式。
> * 建立並執行 HDInsight 腳本動作。
> * 在 HDInsight 叢集上執行適用于 Apache Spark 應用程式的 .NET。

## <a name="prerequisites"></a>必要條件：

開始之前，請執行下列工作：

* 如果您沒有 Azure 訂用帳戶，請建立[免費帳戶](https://azure.microsoft.com/free/)。
* 登入 [Azure 入口網站](https://portal.azure.com/)。
* 在您的[Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409)、 [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)或[MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)電腦上安裝 Azure 儲存體總管。
* 完成[Apache Spark 的 .net-在10分鐘內開始](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)使用教學課程。

## <a name="access-your-storage-accounts"></a>存取您的儲存體帳戶

1. 開啟 Azure 儲存體總管。

2. 選取左側功能表上的 [**新增帳戶**]，然後登入您的 Azure 帳戶。

    ![從儲存體總管登入 Azure 帳戶](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   登入之後，您應該會看到您擁有的所有儲存體帳戶，以及已上傳至儲存體帳戶的任何資源。

## <a name="create-an-hdinsight-cluster"></a>建立 HDInsight 叢集

> [!IMPORTANT]
> HDInsight 叢集的計費是以每分鐘為單位，即使您不使用它們也一樣。 在您完成使用叢集之後，請務必刪除叢集。 如需詳細資訊，請參閱本教學課程的[清理資源](#clean-up-resources)一節。

1. 請造訪[Azure 入口網站](https://portal.azure.com)。

2. 選取 [ **+ 建立資源**]。 然後，從 [**分析**] 類別中選取 [ **HDInsight** ]。

    ![從 Azure 入口網站建立 HDInsight 資源](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. 在 [**基本**] 底下，提供下列值：

    |屬性  |描述  |
    |---------|---------|
    |訂閱  | 從下拉式選單中，選擇其中一個作用中的 Azure 訂用帳戶。 |
    |資源群組 | 指定您要建立新的資源群組，還是使用現有的。 資源群組是保存 Azure 解決方案相關資源的容器。 |
    |叢集名稱 | 提供 HDInsight Spark 叢集的名稱。|
    |位置   | 選取資源群組的 [位置]。 此範本會使用此位置來建立叢集，以及針對預設叢集儲存體。 |
    |叢集類型| 選取 [ **Spark** ] 作為 [叢集類型]。|
    |叢集版本|一旦選取叢集類型，此欄位將會以預設版本自動填入。 選取 [2.3] 或 [2.4] 版本的 Spark。|
    |叢集登入使用者名稱| 輸入叢集登入使用者名稱。  預設名稱為*admin*。 |
    |叢集登入密碼| 輸入任何登入密碼。 |
    |安全殼層（SSH）使用者名稱| 輸入 [SSH 使用者名稱]。 根據預設，此帳戶會與叢集登入使用者*名稱*帳戶共用相同的密碼。 |

4. 選取 **[下一步]：儲存體 > >** 繼續前往 [**儲存體**] 頁面。 在 [**儲存體**] 底下，提供下列值：

    |屬性  |描述  |
    |---------|---------|
    |主要儲存體類型|使用預設值**Azure 儲存體**。|
    |選取方法|使用 [**從清單中選取**預設值]。|
    |主要儲存體帳戶|選擇您的訂用帳戶，以及該訂用帳戶內的其中一個作用中儲存體帳戶。|
    |容器|此容器是儲存體帳戶中的特定 blob 容器，您的叢集會在此尋找檔案以在雲端中執行您的應用程式。 您可以為它提供任何可用的名稱。|

5. 在 [**審查 + 建立**] 底下，選取 [**建立**]。 建立叢集大約需要20分鐘的時間。 您必須先建立叢集，才能繼續進行下一個步驟。

## <a name="publish-your-app"></a>發行您的應用程式

接下來，您會發佈在 .Net 中建立[Apache Spark-開始使用10分鐘](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro)教學課程的*mySparkApp* ，這可讓您的 Spark 叢集存取執行應用程式所需的所有檔案。

1. 執行下列命令以發佈*mySparkApp*：

   **在 Windows 上**：

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   **在 Linux 上：**

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. 請執行下列工作來壓縮已發佈的應用程式檔，讓您可以輕鬆地將它們上傳到您的 HDInsight 叢集。

   **在 Windows 上**：

   流覽至*mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64*。 然後，在 [**發行**資料夾] 上按一下滑鼠右鍵，然後選取 **[傳送至 > 壓縮的（zipped）資料夾**]。 將新資料夾命名為**publish .zip**。

   **在 Linux 上，執行下列命令：**

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a>將檔案上傳至 Azure

接下來，您可以使用 Azure 儲存體總管，將下列五個檔案上傳至您為叢集儲存體選擇的 blob 容器：

* Microsoft. Spark. 背景工作角色
* install-worker.sh
* 發行 .zip
* microsoft-spark-2.3. x-0.3.0 .jar
* 輸入 .txt。

1. 開啟 Azure 儲存體總管，然後從左側功能表流覽至您的儲存體帳戶。 向下切入至儲存體帳戶中**Blob 容器**下的叢集 blob 容器。

2. Apache Spark*可協助執行*您的應用程式，例如您可能已撰寫的任何使用者定義函數（udf）。 下載[Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)。 然後，選取 [**上傳**] Azure 儲存體總管中傳背景工作角色。

   ![將檔案上傳至 Azure 儲存體總管](./media/hdinsight-deployment/upload-files-to-storage.png)

3. *Install-worker.sh*是一個腳本，可讓您將 Apache Spark 相依檔案的 .net 複製到叢集的節點中。

   在您的本機電腦上建立名為**install-worker.sh**的新檔案，並貼上位於 GitHub 的[install-worker.sh 內容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh)。 然後，將*install-worker.sh*上傳至您的 blob 容器。

4. 您的叢集需要包含應用程式已發佈檔案的發佈 .zip 檔案。 流覽至您已發行的資料夾， **mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64**，然後找出**publish. zip**。 然後將*publish*上傳至您的 blob 容器。

5. 您的叢集需要封裝成 jar 檔案的應用程式代碼。 流覽至您已發行的資料夾**mySparkApp/bin/Release/netcoreapp 3.0/ubuntu. 16.04-x64**，然後找出**microsoft-spark-2.3. x-0.3.0。** 然後，將 jar 檔案上傳到您的 blob 容器。

   可能有多個 .jar 檔案（適用于版本 2.3. x 和 2.4. x 版的 Spark）。 您必須選擇與叢集建立期間所選擇的 Spark 版本相符的 .jar 檔案。 例如，如果您在叢集建立期間選擇 Spark 2.3.2，請選擇 [ *microsoft-spark-2.3 x-0.3.0* ]。

6. 您的叢集需要您應用程式的輸入。 流覽至您的**mySparkApp**目錄，並找出 [**輸入 .txt**]。 將您的輸入檔案上傳至 blob 容器中的**使用者/sshuser**目錄。 您將透過 ssh 連線到您的叢集，而此資料夾是您的叢集尋找其輸入的位置。 *輸入 .txt*檔案是上傳至特定目錄的唯一檔案。

## <a name="run-the-hdinsight-script-action"></a>執行 HDInsight 腳本動作

一旦您的叢集正在執行，且您已將檔案上傳至 Azure，您就可以在叢集上執行**install-worker.sh**腳本。

1. 在 Azure 入口網站中，流覽至您的 HDInsight Spark 叢集，然後選取 [**腳本動作**]。

2. 選取 [ **+ 提交新**的]，並提供下列值：

   |屬性  |描述  |
   |---------|---------|
   | 指令碼類型 |自訂|
   | Name | 安裝背景工作|
   | Bash 腳本 URI |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> 若要確認此 URI，請以滑鼠右鍵按一下 Azure 儲存體總管中的 [install-worker.sh]，然後選取 [屬性]。 |
   | 節點類型| 背景工作|
   | 參數 | Azure </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> /usr/local/bin

3. 選取 [**建立**] 以提交您的腳本。

## <a name="run-your-app"></a>執行應用程式

1. 在 Azure 入口網站中，流覽至您的 HDInsight Spark 叢集，然後選取 **[SSH + 叢集登**入]。

2. 複製 ssh 登入資訊，並將登入貼入終端機。 使用您在叢集建立期間所設定的密碼來登入您的叢集。 您應該會看到歡迎您前往 Ubuntu 和 Spark 的訊息。

3. 使用**spark-submit**命令在 HDInsight 叢集上執行您的應用程式。 請記得以您的 blob 容器和儲存體帳戶的實際名稱取代範例腳本中的**mycontainer**和**mystorageaccount** 。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   當您的應用程式執行時，您會看到寫入主控台的「快速入門」本機執行中的相同字數統計表。 恭喜，您已在雲端中執行 Apache Spark 應用程式的第一個 .NET！

## <a name="clean-up-resources"></a>清除資源

HDInsight 會將您的資料儲存在 Azure 儲存體中，因此您可以放心地刪除未使用的叢集。 即使 HDInsight 叢集不在使用中，您也必須支付該叢集的費用。 由於叢集的費用比儲存體費用多倍，因此在不使用叢集的情況下，刪除叢集會變得經濟合理。

您也可以選取資源組名來開啟 [資源群組] 頁面，然後選取 [**刪除資源群組**]。 藉由刪除資源群組，您可以同時刪除 HDInsight Spark 叢集和預設儲存體帳戶。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Azure HDInsight。 若要深入了解 HDInsight，請繼續前往 Azure HDInsight 文件。

> [!div class="nextstepaction"]
> [Azure HDInsight 檔](https://docs.microsoft.com/azure/hdinsight/)
