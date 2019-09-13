---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db374a47140392577872f6635eb7275682a7a547
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928546"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks

本教學課程會教導如何將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 準備 Microsoft.Spark.Worker
> - 發佈您的 Spark .NET 應用程式
> - 將您的應用程式部署到 Databricks
> - 執行應用程式

## <a name="prerequisites"></a>必要條件

開始之前，請執行下列動作：

- 下載 [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)。
- 將 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下載到您的本機電腦。 這是您稍後用來將適用於 Apache Spark 的 .NET 應用程式相依檔案複製到您 Spark 叢集背景工作節點的協助程式指令碼。

## <a name="prepare-worker-dependencies"></a>準備背景工作相依性

**Microsoft.Spark.Worker** 是一種後端元件，存在於您 Spark 叢集的個別背景工作節點上。 當您想要執行 C# UDF (使用者定義函式) 時，Spark 需要了解如何啟動 .NET CLR 來執行 UDF。 **Microsoft.Spark.Worker** 會向 Spark 提供類別集合，其會啟用此功能。

1. 選取要部署在您叢集上的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。

   例如，若您想要使用 `netcoreapp2.1` 的 `.NET for Apache Spark v0.1.0`，您可以下載 [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)。

2. 將 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上傳到您叢集可以存取的分散式檔案系統 (例如 DBFS)。

## <a name="prepare-your-net-for-apache-spark-app"></a>準備適用於 Apache Spark 的 .NET 應用程式

1. 遵循[開始使用](get-started.md)教學課程來建置您的應用程式。

2. 將您的 Spark .NET 應用程式發佈為獨立式應用程式。

   您可以在 Linux 上執行下列命令。

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. 為發佈的檔案產生 `<your app>.zip`。

   您可以使用 `zip`，在 Linux 上執行下列命令。

   ```bash
   zip -r <your app>.zip .
   ```

4. 將下列項目上傳到您叢集可存取的分散式檔案系統 (例如 DBFS)：

   - `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`：此 jar 已作為 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件的一部分包含在其中，且已共置於您應用程式的建置輸出目錄。
   - `<your app>.zip`
   - 要放在每個執行程式中工作目錄的檔案 (例如相依性檔案或每個背景工作都可存取的通用資料) 或組件 (例如包含您使用者定義函式或您應用程式相依程式庫的 DLL)。

## <a name="deploy-to-databricks"></a>部署至 Databricks

[Databricks](https://databricks.com) 是一種平台，提供使用 Apache Spark 的雲端式巨量資料處理。

> [!Note] 
> [Azure Databricks](https://azure.microsoft.com/services/databricks/) 和 [AWS Databricks](https://databricks.com/aws) 都是以 Linux 為基礎。 因此，若您想要將應用程式部署到 Databricks，請確認應用程式與 .NET Standard 相容，且您是使用 [.NET Core 編譯器](https://dotnet.microsoft.com/download)來編譯應用程式。

Databricks 可讓您將適用於 Apache Spark 的 .NET 應用程式部署到現有使用中叢集，或在您每次啟動作業時建立新的叢集。 這需要在您提交適用於 Apache Spark 的 .NET 應用程式前，先安裝 **Microsoft.Spark.Worker**。

### <a name="deploy-microsoftsparkworker"></a>部署 Microsoft.Spark.Worker

針對叢集，此步驟只需要一次。

1. 下載 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) 到您的本機電腦。

2. 修改 **db-init.sh** 以指向您要下載和在您叢集上安裝的 **Microsoft.Spark.Worker** 版本。

3. 安裝 [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)。

4. Databricks CLI 的[設定驗證](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication)詳細資料。

5. 使用下列命令將檔案上傳到您的 Databricks 叢集：

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. 移至您的 Databricks 工作區。 從左側功能表中選取 [Clusters] \(叢集\)，然後選取 [Create Cluster] \(建立叢集\)。

7. 適當地設定叢集後，請設定**初始指令碼**並建立叢集。

   ![指令碼動作影像](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>執行應用程式 

您可以使用 `set JAR` 或 `spark-submit` 來將您的作業提交到 Databricks。

### <a name="use-set-jar"></a>使用 Set JAR

[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) 可讓您將作業提交到現有使用中叢集。

#### <a name="one-time-setup"></a>一次性設定

1. 前往您的 Databricks 叢集，並從左側功能表中選取 [Jobs] \(作業\)。 然後選取 [Set JAR]。

2. 上傳適當的 `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` 檔案。

3. 適當地設定參數。

   ```
   Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. 設定 [Cluster] \(叢集\) 以指向您在前一節中為其建立**初始指令碼**的現有叢集。

#### <a name="publish-and-run-your-app"></a>發佈和執行您的應用程式

1. 使用 [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) 來將應用程式上傳到您的 Databricks 叢集。

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. 此步驟只有在應用程式組件 (例如包含使用者定義函式及其相依性的 DLL) 需要放置在每個 **Microsoft.Spark.Worker** 的工作目錄時才需要。

   - 將應用程式組件上傳到您的 Databricks 叢集
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - 取消註解並修改 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 中的應用程式相依性區段，以指向應用程式相依性路徑並上傳到您的 Databricks 叢集。
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - 重新啟動您的叢集。

3. 前往您位於 Databricks 工作區中的 Databricks 叢集。 在 [Jobs] \(作業\) 下方，選取作業，然後選取 [Run Now] \(立即執行\) 來執行您的作業。

### <a name="use-spark-submit"></a>使用 spark-submit

[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令可讓您將作業提交到新的叢集。

1. [建立作業](https://docs.databricks.com/user-guide/jobs.html)並選取 [Configure spark-submit] \(設定 spark-submit\)。

2. 搭配下列參數設定 `spark-submit`：

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. 前往您位於 Databricks 工作區中的 Databricks 叢集。 在 [Jobs] \(作業\) 下方，選取作業，然後選取 [Run Now] \(立即執行\) 來執行您的作業。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Databricks。 若要深入了解 Databricks，請繼續前往 Azure Databricks 文件。

> [!div class="nextstepaction"]
> [Azure Databricks 文件](https://docs.microsoft.com/azure/azure-databricks/)
