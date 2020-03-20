---
title: 將阿帕奇火花作業的 .NET 提交到資料磚塊
description: 瞭解如何使用火花提交和設置 Jar 將 Apache Spark 的 .NET 作業提交到 Databricks。
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187614"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>將阿帕奇火花作業的 .NET 提交到資料磚塊

有兩種方法可以將的 .NET 用於 Apache Spark 作業部署到`spark-submit`資料磚塊：和"設置 Jar"。

## <a name="deploy-using-spark-submit"></a>使用火花提交進行部署

您可以使用[火花提交](https://spark.apache.org/docs/latest/submitting-applications.html)命令將 Apache Spark 作業的 .NET 提交到資料磚塊。 `spark-submit`只允許提交到按需創建的群集。

1. 導航到資料磚塊工作區並創建作業。 為作業選擇標題，然後選擇 **"配置火花提交**"。 在作業配置中粘貼以下參數，然後選擇 **"確認**"。

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > 根據您的特定檔和配置更新上述參數的內容。 例如，引用您上傳到 DBFS 的 Microsoft.Spark jar 檔的版本，並使用應用和已發佈的應用 ZIP 檔案的適當名稱。

2. 導航到作業並選擇 **"編輯"** 以配置作業的群集。 根據要在部署中使用 Apache Spark 的版本設置資料磚塊執行階段版本。 然後選擇 **"以來"腳本>的高級選項**，並將 Init`dbfs:/spark-dotnet/db-init.sh`腳本路徑設置為 。 選擇 **"確認**"以確認群集設置。

3. 導航到作業，然後選擇 **"立即運行"** 以在新配置的 Spark 群集上運行作業。 創建作業的群集需要幾分鐘時間。 創建作業後，將提交作業。 您可以通過從資料磚塊工作區的左側功能表中選擇 **"群集"** 來查看輸出，然後選擇**驅動程式日誌**。

## <a name="deploy-using-set-jar"></a>使用"設置 Jar"進行部署

或者，您可以使用資料磚塊工作區中的["設置 Jar"](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job)將 Apache Spark 作業的 .NET 提交到資料磚塊。 *Set Jar*允許作業提交到現有活動群集。

### <a name="one-time-setup"></a>單次設定

1. 導航到資料磚塊群集，並從左側功能表中選擇 **"作業"，** 然後**選擇"設置 JAR**"。

2. 上傳相應的`microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`。

3. 修改以下參數以包括您以： 代替發佈的可執行檔的正確名稱`<your-app-name>`：

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. 將群集配置為指向已為其設置 init 腳本的現有群集。

### <a name="publish-and-run-your-app"></a>發佈和執行您的應用程式

1. 確保已發佈應用，並且應用程式代碼不使用`SparkSession.Stop()`。

2. 使用[資料塊 CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli)將應用程式上載到資料磚群集。 例如，使用以下命令將已發佈的應用上載到群集：

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. 如果應用中有任何使用者定義的函數，則需要將應用程式集（如包含使用者定義的函數及其依賴項的 DLL）放置在每個*Microsoft.Spark.Worker*的工作目錄中。

    將應用程式程式集上載到 Databricks 群集：

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    db-init.sh取消注釋並修改應用依賴項[部分，以](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)指向應用依賴項路徑。 然後，將更新*db-init.sh*上載到群集：

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. 導航到**資料磚塊群集>作業> [作業名稱] >立即運行**以運行作業。

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [將 .NET for Apache Spark 應用程式部署到 Databricks](../tutorials/databricks-deployment.md)
* [Azure Databricks 文件](https://docs.microsoft.com/azure/azure-databricks/)
