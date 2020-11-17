---
title: 將 Apache Spark 作業的 .NET 提交至 Databricks
description: 瞭解如何將 Apache Spark 作業的 .NET 提交至使用 Spark 提交和設定 Jar 的 Databricks。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4d37383ccb3c9b311e0fbd0ada195ac20113e505
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688198"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>將 Apache Spark 作業的 .NET 提交至 Databricks

您可以在 Databricks 叢集上執行您的 .NET 以進行 Apache Spark 作業，但它並不是現成可用。 有兩種方式可將 Apache Spark 作業的 .NET 部署至 Databricks： `spark-submit` 和設定 Jar。

## <a name="deploy-using-spark-submit"></a>使用 spark 部署-提交

您可以使用 [spark 提交](https://spark.apache.org/docs/latest/submitting-applications.html) 命令，將 Apache Spark 作業的 .net 提交至 Databricks。 `spark-submit` 只允許提交至隨選建立的叢集。

1. 流覽至您的 Databricks 工作區，並建立作業。 選擇您作業的標題，然後選取 [ **設定 spark-提交**]。 在作業設定中貼上下列參數，然後選取 [ **確認**]。

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > 根據您的特定檔案和設定，更新上述參數的內容。 例如，參考您上傳至 DBFS 的 Microsoft .jar jar 檔案版本，並使用應用程式的適當名稱和已發佈的應用程式 zip 檔。

2. 流覽至您的作業，然後選取 [ **編輯** ] 以設定作業的叢集。 根據您想要在部署中使用的 Apache Spark 版本，設定 Databricks Runtime 版本。 然後選取 [ **Advanced Options > Init** Script]，並將 Init Script Path 設定為 `dbfs:/spark-dotnet/db-init.sh` 。 選取 [ **確認** ] 以確認您的叢集設定。

3. 流覽至您的作業，然後選取 [ **立即執行** ]，在新設定的 Spark 叢集上執行您的作業。 建立作業的叢集需要幾分鐘的時間。 一旦建立之後，您的作業就會提交。 您 **可以從 Databricks** 工作區的左側功能表中選取 [叢集] 來查看輸出，然後選取 [ **驅動程式記錄** 檔]。

## <a name="deploy-using-set-jar"></a>使用 Set Jar 進行部署

或者，您可以在 Databricks 工作區中使用 [Set Jar](/azure/databricks/jobs#--create-a-job) ，將適用于 Apache Spark 作業的 .net 提交給 Databricks。 *Set Jar* 允許將工作提交至現有的使用中叢集。

### <a name="one-time-setup"></a>單次設定

1. 流覽至您的 Databricks 叢集，然後從左側功能表中選取 [ **作業** ]，接著 **設定 [JAR**]。

2. 上傳適當的 `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` 。

3. 修改下列參數，以包含您所發行之可執行檔的正確名稱，以取代 `<your-app-name>` ：

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. 設定叢集以指向您已設定 init 腳本的現有叢集。

### <a name="publish-and-run-your-app"></a>發佈和執行您的應用程式

1. 確定您已發佈您的應用程式，且您的應用程式程式碼未使用 `SparkSession.Stop()` 。

2. 使用 [DATABRICKS CLI](/azure/databricks/dev-tools/databricks-cli) 將應用程式上傳至您的 Databricks 叢集。 例如，使用下列命令，將已發佈的應用程式上傳至您的叢集：

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. 如果您的應用程式中有任何使用者定義函數，則應用程式元件（例如包含使用者定義函式的 Dll 以及其相依性）必須放 *在每個* app.config 的工作目錄中。

    將您的應用程式元件上傳至 Databricks 叢集：

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    取消批註並修改 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 中的應用程式相依性區段，以指向您的應用程式相依性路徑。 然後，將更新的 *db-init.sh* 上傳至您的叢集：

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. 流覽至 **Databricks 叢集 > 作業 > [作業名稱] > 立即執行** 以執行您的作業。

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [將 .NET for Apache Spark 應用程式部署到 Databricks](../tutorials/databricks-deployment.md)
* [Azure Databricks 文件](/azure/azure-databricks/)
