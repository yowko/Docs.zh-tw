---
title: 從 .NET 針對 Apache Spark 應用程式叫用 JAVA Udf
description: 瞭解如何從 .NET 針對 Apache Spark 應用程式呼叫 JAVA UDF。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 17f0ff611e68a5dab2032f78ef75912f314d88a5
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688263"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a>從 .NET 針對 Apache Spark 應用程式呼叫 JAVA UDF

在本文中，您將瞭解如何從 [.net 針對 Apache Spark](https://github.com/dotnet/spark) 應用程式呼叫 JAVA User-Defined 函式 (UDF) 。

1. 如何定義 JAVA Udf 並將它們編譯成 jar-如果您已經在 jar 檔案中定義 UDF，就不需要執行此步驟。 在這種情況下，您只需要包含封裝的 UDF 函式的完整名稱。
2. 在 .NET 中為 Apache Spark 應用程式註冊並呼叫您的 JAVA UDF。

## <a name="define-and-compile-your-java-udfs"></a>定義及編譯您的 JAVA Udf

1. 建立 Maven 或 SBT 專案，並將下列相依性新增至專案設定檔：
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. 根據您 UDF 的簽章來 (建立 [相關的介面](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) ，以定義您的 JAVA UDF) 並匯入相關的套件，如以下簡單範例所示

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. 編譯並封裝您的專案，以建立和可執行檔 jar （例如） `UdfApp-0.0.1.jar` 。

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a>在 .NET 中註冊並呼叫 JAVA Udf 以進行 Apache Spark

1. 使用 [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API 向 SPARK SQL 註冊您的 JAVA UDF。
2. 使用函 `DataFrame` 式，註冊您想要以 SQL 資料表的形式呼叫 UDF 的 [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) 。
3. 您 `SparkSession.Sql` 可以使用 SPARK SQL，在資料表視圖上呼叫 UDF。
說明上述步驟的基本範例：

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. 使用來提交此應用程式， `spark-submit` 方法是透過選項傳遞先前編譯的 JAVA UDF jar `--jars` ：

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-2-4_2.11-1.0.0.jar InterRuntimeUDFs.exe
    ```

    結果資料框架會將 `dfUdf` 數位5新增至輸入資料行的每個資料列，如下所定義 `JavaUdf` ：

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a>在 Apache Spark 中從 Scala 或 Python 呼叫 .NET UDF

您也可以使用 [sparkdotnetudf 開放原始碼工具](https://github.com/imback82/sparkdotnetudf)，從以 Scala 或 Python 撰寫的 Apache Spark 應用程式註冊和叫用 c # UDF。
