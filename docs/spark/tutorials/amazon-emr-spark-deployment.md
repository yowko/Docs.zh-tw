---
title: 將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark
description: 探索如何將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0eea5a40ae4643c7447e2f7281dc8b0db609ca79
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117948"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark

本教學課程會教導如何將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 準備 Microsoft.Spark.Worker
> * 發佈您的 Spark .NET 應用程式
> * 將您的應用程式部署到 Amazon EMR Spark
> * 執行應用程式

## <a name="prerequisites"></a>必要條件

開始之前，請執行下列動作：

* 下載 [AWS CLI](https://aws.amazon.com/cli/)。
* 將 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 下載到您的本機電腦。 這是您稍後用來將適用於 Apache Spark 的 .NET 應用程式相依檔案複製到您 Spark 叢集背景工作節點的協助程式指令碼。

## <a name="prepare-worker-dependencies"></a>準備背景工作相依性

**Microsoft.Spark.Worker** 是一種後端元件，其存在於您 Spark 叢集的個別背景工作節點上。 當您想要執行 C# UDF (使用者定義函式) 時，Spark 需要了解如何啟動 .NET CLR 來執行 UDF。 **Microsoft.Spark.Worker** 會向 Spark 提供類別集合，其會啟用此功能。

1. 選取要部署在您叢集上的 [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp 版本。

   例如，若您想要使用 `netcoreapp2.1` 的 `.NET for Apache Spark v0.1.0`，您可以下載 [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)。

2. 將 `Microsoft.Spark.Worker.<release>.tar.gz` 和 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 上傳到您叢集可以存取的分散式檔案系統 (例如 S3)。

## <a name="prepare-your-net-for-apache-spark-app"></a>準備適用於 Apache Spark 的 .NET 應用程式

1. 遵循[開始使用](get-started.md)教學課程來建置您的應用程式。

2. 將您的 Spark .NET 應用程式發佈為獨立式應用程式。

   在 Linux 上執行下列命令。

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. 為發佈的檔案產生 `<your app>.zip`。

   使用 `zip` 在 Linux 上執行下列命令。

   ```bash
   zip -r <your app>.zip .
   ```

4. 將下列項目上傳到您叢集可存取的分散式檔案系統 (例如 S3)：

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`：此 jar 已作為 [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 套件的一部分包含在其中，且已共置於您應用程式的建置輸出目錄。
   * `<your app>.zip`
   * 要放在每個執行程式中工作目錄的檔案 (例如相依性檔案或每個背景工作都可存取的通用資料) 或組件 (例如包含您使用者定義函式或您應用程式相依程式庫的 DLL)。

## <a name="deploy-to-amazon-emr-spark"></a>部署至 Amazon EMR Spark

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) 是一種受控叢集平台，其簡化在 AWS 上執行巨量資料架構。

> [!NOTE] 
> Amazon EMR Spark 是以 Linux 為基礎。 因此，若您想要將應用程式部署到 Amazon EMR Spark，請確認應用程式與 .NET Standard 相容，且您是使用 [.NET Core 編譯器](https://dotnet.microsoft.com/download)來編譯應用程式。

### <a name="deploy-microsoftsparkworker"></a>部署 Microsoft.Spark.Worker

僅在建立叢集時才需要此步驟。

使用[啟動程序動作](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)在叢集建立期間執行 `install-worker.sh`。

使用 AWS CLI 在 Linux 上執行下列命令。

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>執行應用程式

有兩種方式可以在 Amazon EMR Spark 上執行您的應用程式：spark-submit 和 Amazon EMR 步驟。

### <a name="use-spark-submit"></a>使用 spark-submit

您可以使用 [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) 命令將適用於 Apache Spark 的 .NET 作業提交到 Amazon EMR Spark。

1. `ssh` 到叢集中的其中一個節點。

2. 執行 `spark-submit`。

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>使用 Amazon EMR 步驟

[Amazon EMR 步驟](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html)可以用來將作業提交到 EMR 叢集上安裝的 Spark 架構。

使用 AWS CLI 在 Linux 上執行下列命令。

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已將適用於 Apache Spark 的 .NET 應用程式部署到 Amazon EMR Spark。 如需適用於 Apache Spark 的 .NET 範例專案，請繼續前往 GitHub。

> [!div class="nextstepaction"]
> [適用於 Apache Spark 的 .NET 範例](https://github.com/dotnet/spark/tree/master/examples)
