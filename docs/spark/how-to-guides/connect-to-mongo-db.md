---
title: 將適用于 Apache Spark 的 .NET 連線到 MongoDB
description: 瞭解如何從 .NET 針對 Apache Spark 應用程式連線到您的 MongoDB 實例。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4cb78998ddb54621a84e9d224a814047e3c40246
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877843"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a><span data-ttu-id="dcced-103">將適用于 Apache Spark 的 .NET 連線到 MongoDB</span><span class="sxs-lookup"><span data-stu-id="dcced-103">Connect .NET for Apache Spark to MongoDB</span></span>

<span data-ttu-id="dcced-104">在本文中，您將瞭解如何從 .NET 針對 Apache Spark 應用程式連接到 MongoDB 實例。</span><span class="sxs-lookup"><span data-stu-id="dcced-104">In this article, you learn how to connect to a MongoDB instance from your .NET for Apache Spark application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dcced-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="dcced-105">Prerequisites</span></span>

1. <span data-ttu-id="dcced-106">將 MongoDB 伺服器啟動並執行，並在其中加入一個 [資料庫，](https://docs.mongodb.com/manual/core/databases-and-collections/) (為本機伺服器下載 [此台伺服器](https://www.mongodb.com/try/download/community) ，或者您可以嘗試使用 [MongoDB](https://www.mongodb.com/cloud/atlas) 的 mongodb 服務。 ) </span><span class="sxs-lookup"><span data-stu-id="dcced-106">Have a MongoDB server up and running with a [database and some collection](https://docs.mongodb.com/manual/core/databases-and-collections/) added to it (Download [this community server](https://www.mongodb.com/try/download/community) for a local server or you can try [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud MongoDB service.)</span></span>

## <a name="set-up-your-mongodb-instance"></a><span data-ttu-id="dcced-107">設定您的 MongoDB 實例</span><span class="sxs-lookup"><span data-stu-id="dcced-107">Set up your MongoDB instance</span></span>

<span data-ttu-id="dcced-108">若要取得 Apache Spark 的 .NET 以與您的 MongoDB 實例通訊，您必須執行下列動作，以確定其已正確設定：</span><span class="sxs-lookup"><span data-stu-id="dcced-108">In order to get .NET for Apache Spark to talk to your MongoDB instance you need to make sure it is set up correctly by doing the following:</span></span>

1. <span data-ttu-id="dcced-109">為您的應用程式建立使用者名稱和密碼以進行連線，並透過 mongo shell 使用下列命令為使用者提供必要的許可權/角色：</span><span class="sxs-lookup"><span data-stu-id="dcced-109">Create a username and password for your application to connect through, and give the user the necessary permissions/roles using the following command through mongo shell:</span></span>

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

2. <span data-ttu-id="dcced-110">確定您的 .NET for Apache Spark 應用程式執行所在的電腦 IP 位址已列入允許清單，以便 MongoDB 伺服器能夠連線。</span><span class="sxs-lookup"><span data-stu-id="dcced-110">Make sure the IP address of the machine your .NET for Apache Spark application is running on is whitelisted for the MongoDB server to be able to connect to.</span></span> <span data-ttu-id="dcced-111">您可以參考 [本指南](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) 來瞭解如何進行。</span><span class="sxs-lookup"><span data-stu-id="dcced-111">You can refer to [this guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to learn how to do that.</span></span>

## <a name="configure-your-net-for-apache-spark-application"></a><span data-ttu-id="dcced-112">設定您的 .NET 以 Apache Spark 應用程式</span><span class="sxs-lookup"><span data-stu-id="dcced-112">Configure your .NET for Apache Spark application</span></span>

1. <span data-ttu-id="dcced-113">設定下列變數，以設定您的應用程式與 MongoDB 實例通訊，並從集合讀取。</span><span class="sxs-lookup"><span data-stu-id="dcced-113">Have the following variables set to configure your application to talk to the MongoDB instance and read from a collection.</span></span>
    1. <span data-ttu-id="dcced-114">**authURI**：「授權您的應用程式連接到所需 MongoDB 實例的連接字串」。</span><span class="sxs-lookup"><span data-stu-id="dcced-114">**authURI**: "Connection string authorizing your application to connect to the required MongoDB instance".</span></span> <span data-ttu-id="dcced-115">的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="dcced-115">The format for that is as follows:</span></span>

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. <span data-ttu-id="dcced-116">使用者**名稱**：您在上一節的步驟1中建立之帳戶的使用者名稱</span><span class="sxs-lookup"><span data-stu-id="dcced-116">**username**: Username of the account you created in Step 1 of the previous section</span></span>
    3. <span data-ttu-id="dcced-117">**密碼**：建立之使用者帳戶的密碼</span><span class="sxs-lookup"><span data-stu-id="dcced-117">**password**: Password of the user account created</span></span>
    4. <span data-ttu-id="dcced-118">**cluster_address**： MongoDB 叢集的主機名稱/位址</span><span class="sxs-lookup"><span data-stu-id="dcced-118">**cluster_address**: hostname/address of your MongoDB cluster</span></span>
    5. <span data-ttu-id="dcced-119">**資料庫**：您要連接的 MongoDB 資料庫</span><span class="sxs-lookup"><span data-stu-id="dcced-119">**database**: The MongoDB database you want to connect to</span></span>
    6. <span data-ttu-id="dcced-120">**集合**：您要讀取的 MongoDB 集合。</span><span class="sxs-lookup"><span data-stu-id="dcced-120">**collection**: The MongoDB collection you want to read.</span></span> <span data-ttu-id="dcced-121"> (在此範例中，我們會使用 [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) 每個 Apache Spark 安裝所提供的標準範例檔案。 ) </span><span class="sxs-lookup"><span data-stu-id="dcced-121">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.)</span></span>

2. <span data-ttu-id="dcced-122">使用 `com.mongodb.spark.sql.DefaultSource` 格式如下 `spark.Read()` 所示的簡單程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="dcced-122">Use the `com.mongodb.spark.sql.DefaultSource` format is `spark.Read()` as shown below in a simple code snippet:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="dcced-123">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="dcced-123">Run your application</span></span>

<span data-ttu-id="dcced-124">若要執行 Apache Spark 應用程式的 .NET，您應該在 `mongo-spark-connector` Spark 專案中將模組定義為組建定義的一部分，並 `libraryDependency` 在 `build.sbt` sbt 專案中使用。</span><span class="sxs-lookup"><span data-stu-id="dcced-124">In order to run your .NET for Apache Spark application, you should define the `mongo-spark-connector` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="dcced-125">針對 (或) 這類 Spark 環境 `spark-submit` `spark-shell` ，您應該使用 `--packages` 命令列選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dcced-125">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<version>.jar yourApp.exe
```

> [!NOTE]
> <span data-ttu-id="dcced-126">請務必根據執行中的 Spark 版本包含套件版本。</span><span class="sxs-lookup"><span data-stu-id="dcced-126">Make sure to include the package version in accordance with the version of Spark being run.</span></span>

<span data-ttu-id="dcced-127">顯示的結果是資料框架 (`df`) 如下所示：</span><span class="sxs-lookup"><span data-stu-id="dcced-127">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
