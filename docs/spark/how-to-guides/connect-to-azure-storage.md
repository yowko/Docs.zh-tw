---
title: 從您的本機電腦連接到遠端存放裝置
description: 使用 .NET 連接到 Azure 儲存體帳戶，以便從本機電腦進行 Apache Spark。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dc0c3b44279756596f3d456616821e690710ae04
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224013"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a>連接到 Azure Data Lake Storage Gen 2 或 WASB 帳戶

在本文中，您將瞭解如何透過 .Net 的實例（適用于在本機 Windows 電腦上執行 [的 (](https://github.com/dotnet/spark) ），連接到 AZURE DATA LAKE STORAGE (ADLS) Gen 2 或 Windows AZURE 儲存體 BLOB) WASB Apache Spark 帳戶。

## <a name="set-up-the-environment"></a>設定環境

1. 從 [官方網站](https://archive.apache.org/dist/spark/) 下載沒有 Hadoop 的 Apache Spark 散發套件 (選擇 [.net 針對 Apache Spark) 所支援](https://github.com/dotnet/spark#supported-apache-spark) 的版本，並將它解壓縮至目錄。 將環境變數設定 `SPARK_HOME` 為這個目錄。
2. 從 [這裡](http://hadoop.apache.org/releases.html) 下載 Apache Hadoop 二進位檔，並將其解壓縮到資料夾，並將您的 `HADOOP_HOME` 環境變數設定為此資料夾。
3. `winutils.exe` `hadoop.dll` 根據上一個步驟中安裝的 Hadoop 版本，從[這個位置](https://github.com/cdarlint/winutils)下載和檔案 () 並將它們放在 hadoop 的 bin 資料夾中。 在 Windows 上需要這些二進位檔，才能正確設定所有專案 (這在) 的 [Apache wiki](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems) 中有詳細的說明。
4. 對您的檔案進行下列變更，以設定您的 Hadoop 安裝 `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` ：
    1. `JAVA_HOME`使用 DOS 路徑設定屬性 (，因為 Hadoop 不像) 中的空格 `JAVA_HOME` 。 這看起來應該像這樣： `C:\Progra~1\Java\jdk1.8.0_241` (指向您在本機電腦上安裝的任何 JAVA 版本) 。
    2. 附加 `%HADOOP_HOME%\share\hadoop\tools\lib\*` 至 `HADOOP_CLASSPATH` 。
    您的最終檔案 `hadoop-env.cmd` 看起來應該像這樣：

    ![最終的 hadoop-env .cmd 檔案](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a>在 Hadoop 中設定儲存體帳戶

1. 開啟您想要透過[Azure 入口網站](https://portal.azure.com)連接的 ADLS Gen 2 或 WASB 儲存體帳戶，然後開啟 [**設定**] 分頁底下的 [**存取金鑰**] 面板，然後從 [key1] 下複製 [**金鑰**] 的值。
2. 現在為了設定 Hadoop 來存取您的 ADLS Gen2 帳戶，您必須編輯 `core-site.xml` 位於 ) 檔案中的 (， `%HADOOP_HOME%\etc\hadoop\` 其中包含整個叢集的設定。 在此檔案的標記內新增下列屬性 `<configuration>` ：

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

    如果您嘗試連接到 WASB 帳戶，請 `dfs` `blob` 在屬性名稱中取代為。 例如： `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net` 。
3. 您可以從您的目錄執行下列命令，以測試從 Hadoop 至儲存體帳戶的連線能力 `%HADOOP_HOME%` ：

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

這應該會顯示 URI 所提供路徑中所有檔案/資料夾的清單。

> [!NOTE]
> 將 URI 衍生給儲存體帳戶的格式如下：
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a>連接到您的儲存體帳戶

1. 如果上述命令正常運作，您現在可以繼續透過 Spark 存取此儲存體帳戶。 先 `hadoop classpath` 從中的命令列執行命令 `%HADOOP_HOME%` ，然後複製輸出。
2. 將步驟1中執行之命令的輸出設定為環境變數的值 `SPARK_DIST_CLASSPATH` 。
3. 現在，您應該能夠使用 abfs URI 透過 Spark .NET 來存取 ADLS 或 WASB 儲存體帳戶，如下列簡單範例所示。  (在此範例中，我們會使用 [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) 每個 Apache Spark 安裝所提供的標準範例檔案。 ) ：

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    顯示的結果是資料框架 (`df`) 如下所示：

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
