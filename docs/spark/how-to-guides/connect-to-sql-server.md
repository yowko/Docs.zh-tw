---
title: 將適用于 Apache Spark 的 .NET 連接至 SQL Server
description: 瞭解如何從 .NET for Apache Spark 應用程式連接至 SQL Server 實例。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: b20710000d8717b5df238aa9a782371fbe586037
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224023"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a>將適用于 Apache Spark 的 .NET 連接至 SQL Server

在本文中，您將瞭解如何從 [.net 針對 Apache Spark](https://github.com/dotnet/spark) 應用程式連接至 SQL server 實例。

## <a name="configure-sql-server-to-grant-your-application-access"></a>設定 SQL Server 以授與應用程式存取權

1. 將登入使用者和密碼新增至 SQL Server 實例的 SQL Server 驗證。
2. 在相關的資料庫層級授與該登入使用者必要的許可權，如下所示：

    ![SQL Server 權限](./media/connect-external-sources/SqlServerAuth.png)

3. 請確定允許 SQL Server 的預設埠 `1433` 通過防火牆。
4. 開啟 [SQL 設定管理員]，透過網路設定啟用 TCP/IP，如下所示：

    ![SQL Server TCP/IP 啟用](./media/connect-external-sources/SqlServerTCPIP.png)

    另外也請注意 [**通訊協定**] 下的 [**全部接聽**] 索引標籤的值。

5. 如果設定為，則針對所有必要的 IP 位址，將 TCP/IP 通訊埠設定為 1433 `Listen All` `No` 。 否則，請在 IPAll 中設定 TCP 埠。

    ![SQL Server TCP/IP 埠](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a>從您的應用程式連接到 SQL Server

1. 使用 Microsoft JDBC Driver for SQL Server 透過您的應用程式提供資料庫連接， (從此 [官方網站](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)) 下載。
2. 設定下列設定，以從您的應用程式連接到 SQL server 實例和資料庫：
    1. **connection_url**：這是用來連接到 SQL server 實例/資料庫的 url，其格式如下：

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. **dbtable**：要存取的資料表名稱。
    3. **使用者**：在設定 SQL Server 的步驟1中設定登入使用者。
    4. **密碼**：在設定 SQL Server 的步驟1中設定的使用者密碼。
3. 在您的應用程式程式碼中使用上述設定，以讀取資料表中的資料，如下所示：

    ```csharp
    static void Main()
    {
        SparkSession spark = SparkSession
            .Builder()
            .AppName("Connect to SQL Server")
            .GetOrCreate();

        string connection_url = "<URL to connect to SQL server instance>";
        string dbtable = "<database table to access>";
        string user = "<Login user name>";
        string password = "<Login user password>";

        DataFrame jdbcDF = spark.Read()
            .Format("jdbc")
            .Option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
            .Option("url", connection_url)
            .Option("dbtable", dbtable)
            .Option("user", user)
            .Option("password", password).Load();
        jdbcDF.Show(); // Displays the content of the SQL table as a DataFrame
    }
    ```
