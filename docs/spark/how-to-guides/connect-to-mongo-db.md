---
title: 將適用于 Apache Spark 的 .NET 連線到 MongoDB
description: 瞭解如何從 .NET 針對 Apache Spark 應用程式連線到您的 MongoDB 實例。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 945e494e8a027d438bf4659d989da6033a13f6f0
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687599"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a>將適用于 Apache Spark 的 .NET 連線到 MongoDB

在本文中，您將瞭解如何從 .NET 針對 Apache Spark 應用程式連接到 MongoDB 實例。

## <a name="prerequisites"></a>先決條件

1. 將 MongoDB 伺服器啟動並執行，並在其中加入一個 [資料庫，](https://docs.mongodb.com/manual/core/databases-and-collections/) (為本機伺服器下載 [此台伺服器](https://www.mongodb.com/try/download/community) ，或者您可以嘗試使用 [MongoDB](https://www.mongodb.com/cloud/atlas) 的 mongodb 服務。 ) 

## <a name="set-up-your-mongodb-instance"></a>設定您的 MongoDB 實例

若要取得 Apache Spark 的 .NET 以與您的 MongoDB 實例通訊，您必須執行下列動作，以確定其已正確設定：

1. 為您的應用程式建立使用者名稱和密碼以進行連線，並透過 mongo shell 使用下列命令為使用者提供必要的許可權/角色：

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. 確定您的 .NET for Apache Spark 應用程式執行所在的電腦 IP 位址已列入允許清單，以便 MongoDB 伺服器能夠連線。 您可以參考 [本指南](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) 來瞭解如何進行。

## <a name="configure-your-net-for-apache-spark-application"></a>設定您的 .NET 以 Apache Spark 應用程式

1. 設定下列變數，以設定您的應用程式與 MongoDB 實例通訊，並從集合讀取。
    1. **authURI**：「授權您的應用程式連接到所需 MongoDB 實例的連接字串」。 的格式如下所示：

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. 使用者 **名稱**：您在上一節的步驟1中建立之帳戶的使用者名稱
    3. **密碼**：建立之使用者帳戶的密碼
    4. **cluster_address**： MongoDB 叢集的主機名稱/位址
    5. **資料庫**：您要連接的 MongoDB 資料庫
    6. **集合**：您要讀取的 MongoDB 集合。  (在此範例中，我們會使用 [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) 每個 Apache Spark 安裝所提供的標準範例檔案。 ) 

2. 使用 `com.mongodb.spark.sql.DefaultSource` 格式如下 `spark.Read()` 所示的簡單程式碼片段：

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a>執行您的應用程式

若要執行 Apache Spark 應用程式的 .NET，您應該在 `mongo-spark-connector` Spark 專案中將模組定義為組建定義的一部分，並 `libraryDependency` 在 `build.sbt` sbt 專案中使用。 針對 (或) 這類 Spark 環境 `spark-submit` `spark-shell` ，您應該使用 `--packages` 命令列選項，如下所示：

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> 請務必根據執行中的 Spark 版本包含套件版本。

顯示的結果是資料框架 (`df`) 如下所示：

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
