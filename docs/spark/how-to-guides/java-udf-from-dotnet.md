---
title: 從 .NET 針對 Apache Spark 應用程式叫用 JAVA Udf
description: 瞭解如何從 .NET 針對 Apache Spark 應用程式呼叫 JAVA UDF。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: edf525102bf5503dcb51247b5fa590aa0d42b369
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224113"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="56f8e-103">從 .NET 針對 Apache Spark 應用程式呼叫 JAVA UDF</span><span class="sxs-lookup"><span data-stu-id="56f8e-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="56f8e-104">在本文中，您將瞭解如何從 [.net 針對 Apache Spark](https://github.com/dotnet/spark) 應用程式呼叫 JAVA User-Defined 函式 (UDF) 。</span><span class="sxs-lookup"><span data-stu-id="56f8e-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="56f8e-105">如何定義 JAVA Udf 並將它們編譯成 jar-如果您已經在 jar 檔案中定義 UDF，就不需要執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="56f8e-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="56f8e-106">在這種情況下，您只需要包含封裝的 UDF 函式的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="56f8e-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="56f8e-107">在 .NET 中為 Apache Spark 應用程式註冊並呼叫您的 JAVA UDF。</span><span class="sxs-lookup"><span data-stu-id="56f8e-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="56f8e-108">定義及編譯您的 JAVA Udf</span><span class="sxs-lookup"><span data-stu-id="56f8e-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="56f8e-109">建立 Maven 或 SBT 專案，並將下列相依性新增至專案設定檔：</span><span class="sxs-lookup"><span data-stu-id="56f8e-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="56f8e-110">根據您 UDF 的簽章來 (建立 [相關的介面](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) ，以定義您的 JAVA UDF) 並匯入相關的套件，如以下簡單範例所示</span><span class="sxs-lookup"><span data-stu-id="56f8e-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

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

3. <span data-ttu-id="56f8e-111">編譯並封裝您的專案，以建立和可執行檔 jar （例如） `UdfApp-0.0.1.jar` 。</span><span class="sxs-lookup"><span data-stu-id="56f8e-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="56f8e-112">在 .NET 中註冊並呼叫 JAVA Udf 以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="56f8e-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="56f8e-113">使用 [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API 向 SPARK SQL 註冊您的 JAVA UDF。</span><span class="sxs-lookup"><span data-stu-id="56f8e-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="56f8e-114">使用函 `DataFrame` 式，註冊您想要以 SQL 資料表的形式呼叫 UDF 的 [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) 。</span><span class="sxs-lookup"><span data-stu-id="56f8e-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="56f8e-115">您 `SparkSession.Sql` 可以使用 SPARK SQL，在資料表視圖上呼叫 UDF。</span><span class="sxs-lookup"><span data-stu-id="56f8e-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="56f8e-116">說明上述步驟的基本範例：</span><span class="sxs-lookup"><span data-stu-id="56f8e-116">A basic example to illustrate the above steps:</span></span>

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

4. <span data-ttu-id="56f8e-117">使用來提交此應用程式， `spark-submit` 方法是透過選項傳遞先前編譯的 JAVA UDF jar `--jars` ：</span><span class="sxs-lookup"><span data-stu-id="56f8e-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-3.0.x-0.12.1.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="56f8e-118">結果資料框架會將 `dfUdf` 數位5新增至輸入資料行的每個資料列，如下所定義 `JavaUdf` ：</span><span class="sxs-lookup"><span data-stu-id="56f8e-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="56f8e-119">在 Apache Spark 中從 Scala 或 Python 呼叫 .NET UDF</span><span class="sxs-lookup"><span data-stu-id="56f8e-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="56f8e-120">您也可以使用 [sparkdotnetudf 開放原始碼工具](https://github.com/imback82/sparkdotnetudf)，從以 Scala 或 Python 撰寫的 Apache Spark 應用程式註冊和叫用 c # UDF。</span><span class="sxs-lookup"><span data-stu-id="56f8e-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
