---
title: 從您的本機電腦連接到遠端存放裝置
description: 使用 .NET 連接到 Azure 儲存體帳戶，以便從本機電腦進行 Apache Spark。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 09e92b0cae848f9c98b691a11842f131f613396b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877841"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a><span data-ttu-id="9e5fd-103">連接到 Azure Data Lake Storage Gen 2 或 WASB 帳戶</span><span class="sxs-lookup"><span data-stu-id="9e5fd-103">Connect to Azure Data Lake Storage Gen 2 or WASB account</span></span>

<span data-ttu-id="9e5fd-104">在本文中，您將瞭解如何透過 .Net 的實例（適用于在本機 Windows 電腦上執行 [的 (](https://github.com/dotnet/spark) ），連接到 AZURE DATA LAKE STORAGE (ADLS) Gen 2 或 Windows AZURE 儲存體 BLOB) WASB Apache Spark 帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-104">In this article, you learn how to connect to an Azure Data Lake Storage (ADLS) Gen 2 or Windows Azure Storage Blob (WASB) account through an instance of [.NET for Apache Spark](https://github.com/dotnet/spark) running locally on your Windows machine.</span></span>

## <a name="set-up-the-environment"></a><span data-ttu-id="9e5fd-105">設定環境</span><span class="sxs-lookup"><span data-stu-id="9e5fd-105">Set up the environment</span></span>

1. <span data-ttu-id="9e5fd-106">從 [官方網站](https://archive.apache.org/dist/spark/) 下載沒有 Hadoop 的 Apache Spark 散發套件 (選擇 [.net 針對 Apache Spark) 所支援](https://github.com/dotnet/spark#supported-apache-spark) 的版本，並將它解壓縮至目錄。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-106">Download the Apache Spark distribution built without Hadoop from [official website](https://archive.apache.org/dist/spark/) (choose a version [supported by .NET for Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)), and extract it to a directory.</span></span> <span data-ttu-id="9e5fd-107">將環境變數設定 `SPARK_HOME` 為這個目錄。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-107">Set the environment variable `SPARK_HOME` to this directory.</span></span>
2. <span data-ttu-id="9e5fd-108">從 [這裡](http://hadoop.apache.org/releases.html) 下載 Apache Hadoop 二進位檔，並將其解壓縮到資料夾，並將您的 `HADOOP_HOME` 環境變數設定為此資料夾。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-108">Download the Apache Hadoop binary from [here](http://hadoop.apache.org/releases.html) and extract to a folder, and set your `HADOOP_HOME` environment variable to this folder.</span></span>
3. <span data-ttu-id="9e5fd-109">`winutils.exe` `hadoop.dll` 根據上一個步驟中安裝的 Hadoop 版本，從[這個位置](https://github.com/cdarlint/winutils)下載和檔案 () 並將它們放在 hadoop 的 bin 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-109">Download the `winutils.exe` and `hadoop.dll` files from [this location](https://github.com/cdarlint/winutils) (depending on the version of Hadoop installed in the previous step) and put them in the bin folder of your Hadoop.</span></span> <span data-ttu-id="9e5fd-110">在 Windows 上需要這些二進位檔，才能正確設定所有專案 (這在) 的 [Apache wiki](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems) 中有詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-110">These binaries are needed on Windows in order to get everything setup correctly (this is explained in detail in the [Apache wiki here](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span></span>
4. <span data-ttu-id="9e5fd-111">對您的檔案進行下列變更，以設定您的 Hadoop 安裝 `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` ：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-111">Configure your Hadoop installation by making the following changes to your `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` file:</span></span>
    1. <span data-ttu-id="9e5fd-112">`JAVA_HOME`使用 DOS 路徑設定屬性 (，因為 Hadoop 不像) 中的空格 `JAVA_HOME` 。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-112">Set the `JAVA_HOME` property using the DOS path (since Hadoop doesn't like spaces in `JAVA_HOME`).</span></span> <span data-ttu-id="9e5fd-113">這看起來應該像這樣： `C:\Progra~1\Java\jdk1.8.0_241` (指向您在本機電腦上安裝的任何 JAVA 版本) 。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-113">This should look something like this: `C:\Progra~1\Java\jdk1.8.0_241` (Pointing to whatever version of Java you have installed on your local machine).</span></span>
    2. <span data-ttu-id="9e5fd-114">附加 `%HADOOP_HOME%\share\hadoop\tools\lib\*` 至 `HADOOP_CLASSPATH` 。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-114">Append `%HADOOP_HOME%\share\hadoop\tools\lib\*` to `HADOOP_CLASSPATH`.</span></span>
    <span data-ttu-id="9e5fd-115">您的最終檔案 `hadoop-env.cmd` 看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-115">Your final `hadoop-env.cmd` file should look something like this:</span></span>

    ![最終的 hadoop-env .cmd 檔案](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a><span data-ttu-id="9e5fd-117">在 Hadoop 中設定儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="9e5fd-117">Configure your storage account in Hadoop</span></span>

1. <span data-ttu-id="9e5fd-118">開啟您想要透過[Azure 入口網站](https://portal.azure.com)連接的 ADLS Gen 2 或 WASB 儲存體帳戶，然後開啟 [**設定**] 分頁底下的 [**存取金鑰**] 面板，然後從 [key1] 下複製 [**金鑰**] 的值。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-118">Open the ADLS Gen 2 or WASB storage account you want to connect to through the [Azure portal](https://portal.azure.com) and open the **Access keys** panel under the **Settings** blade and copy the value of **Key** from under key1.</span></span>
2. <span data-ttu-id="9e5fd-119">現在為了設定 Hadoop 來存取您的 ADLS Gen2 帳戶，您必須編輯 `core-site.xml` 位於 ) 檔案中的 (， `%HADOOP_HOME%\etc\hadoop\` 其中包含整個叢集的設定。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-119">Now in order to configure Hadoop to access your ADLS Gen2 account you would have to edit your `core-site.xml` (located in `%HADOOP_HOME%\etc\hadoop\` ) file which contains cluster-wide configuration.</span></span> <span data-ttu-id="9e5fd-120">在此檔案的標記內新增下列屬性 `<configuration>` ：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-120">Add the following properties inside the `<configuration>` tags in this file:</span></span>

    ```xml
    <configuration>
      <property>
        <name>fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>SharedKey</value>
        <description></description>
      </property>
      <property>
        <name>fs.azure.account.key.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>YOUR ACCESS KEY (copied from Step 1)</value>
        <description>The secret password. Never share these.</description>
      </property>
    </configuration>
    ```

    <span data-ttu-id="9e5fd-121">如果您嘗試連接到 WASB 帳戶，請 `dfs` `blob` 在屬性名稱中取代為。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-121">If you are trying to connect to a WASB account, replace `dfs` with `blob` in the property names.</span></span> <span data-ttu-id="9e5fd-122">例如： `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net` 。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-122">For example, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span></span>
3. <span data-ttu-id="9e5fd-123">您可以從您的目錄執行下列命令，以測試從 Hadoop 至儲存體帳戶的連線能力 `%HADOOP_HOME%` ：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-123">You can test the connectivity to your Storage Account from Hadoop by running the following command from your `%HADOOP_HOME%` directory:</span></span>

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

<span data-ttu-id="9e5fd-124">這應該會顯示 URI 所提供路徑中所有檔案/資料夾的清單。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-124">This should display a list of all files/folders in the path provided by your URI.</span></span>

> [!NOTE]
> <span data-ttu-id="9e5fd-125">將 URI 衍生給儲存體帳戶的格式如下：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-125">The format to derive the URI to your Storage account is as follows:</span></span>
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a><span data-ttu-id="9e5fd-126">連接到您的儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="9e5fd-126">Connect to your storage account</span></span>

1. <span data-ttu-id="9e5fd-127">如果上述命令正常運作，您現在可以繼續透過 Spark 存取此儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-127">If the above command worked, you can now move on to accessing this storage account through Spark.</span></span> <span data-ttu-id="9e5fd-128">先 `hadoop classpath` 從中的命令列執行命令 `%HADOOP_HOME%` ，然後複製輸出。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-128">First run the command `hadoop classpath` from the commandline inside `%HADOOP_HOME%` and copy the output.</span></span>
2. <span data-ttu-id="9e5fd-129">將步驟1中執行之命令的輸出設定為環境變數的值 `SPARK_DIST_CLASSPATH` 。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-129">Set the output of the command run in Step 1 to the value of environment variable `SPARK_DIST_CLASSPATH`.</span></span>
3. <span data-ttu-id="9e5fd-130">現在，您應該能夠使用 abfs URI 透過 Spark .NET 來存取 ADLS 或 WASB 儲存體帳戶，如下列簡單範例所示。</span><span class="sxs-lookup"><span data-stu-id="9e5fd-130">Now you should be able to access your ADLS or WASB storage account through Spark .NET using the abfs URI as shown in the simple example below.</span></span> <span data-ttu-id="9e5fd-131"> (在此範例中，我們會使用 [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) 每個 Apache Spark 安裝所提供的標準範例檔案。 ) ：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-131">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.):</span></span>

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    <span data-ttu-id="9e5fd-132">顯示的結果是資料框架 (`df`) 如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e5fd-132">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
