---
title: 針對 Apache Spark 的互動式環境，在 .NET 中撰寫和呼叫 Udf。
description: 瞭解如何在 .NET 中撰寫和呼叫 Udf 來 Apache Spark 互動式 shell。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: d02ce7ec92ac1758b490b66d241d4957082eb20e
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877876"
---
# <a name="write-and-call-udfs-in-net-for-apache-spark-interactive-environments"></a>針對 Apache Spark 互動式環境在 .NET 中撰寫和呼叫 Udf

在本文中，您將瞭解如何在 .NET 中使用使用者定義函式 (Udf) ，以 Apache Spark 互動式環境。

## <a name="prerequisites"></a>必要條件

1. 安裝 [.Net Interactive](https://github.com/dotnet/interactive)
2. 安裝 [Jupyter lab](https://jupyter.org/)

## <a name="net-for-apach-spark-interactive-experience"></a>適用于 Apach Spark 互動式體驗的 .NET

[.Net for Apache Spark](https://github.com/dotnet/spark) 使用 [.Net Interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) 提供 Spark 內互動式體驗的 .net 支援。 若要瞭解如何設定環境以嘗試搭配 Jupyter 筆記本使用 .NET Interactive，請參閱 [.Net 互動式儲存](https://github.com/dotnet/interactive)機制。

此外，建議您 [在 .net 中進行 UDF 序列化 Apache Spark 的相關文章](udf-guide.md) ，以瞭解什麼是 udf，以及它們如何在 .net 中序列化以進行 Apache Spark。
本指南使用 Jupyter 筆記本來說明如何在互動式體驗中使用 Udf。

## <a name="define-a-udf-in-net-interactive"></a>以 .NET 互動定義 UDF

在互動式體驗中，您可以將資料格視為在 [複寫的某個](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)反復專案中提交的程式碼片段。 例如，看看下列筆記本以瞭解這代表什麼意思：

![Jupyter Notebook 資料格](./media/dotnet-interactive/dotnet-interactive-cells.png)

以紅色箭號標記的每個區塊都是一個資料格或一個將程式碼提交至 Spark 的資料格。 現在，定義參考自訂使用者定義物件的 UDF 時，必須在定義其所參考物件的相同資料格中定義 UDF。 讓我們看看看起來像這樣的範例：

![正常運作的 UDF](./media/dotnet-interactive/working-udf.png)

## <a name="call-a-udf-on-a-dataframe"></a>呼叫資料框架上的 UDF

在上呼叫之前定義的 UDF 時， `DataFrame` 請務必確定 UDF 是在先前提交的儲存格中定義，然後再呼叫它，如先前範例中所示。

現在讓我們看看在定義該 UDF 的相同儲存格中呼叫 UDF 會發生什麼事。

![失敗的 UDF 呼叫](./media/dotnet-interactive/udf_fails.png)

上述反白顯示的錯誤是因為 UDF 元件必須先經過編譯並傳送給背景工作角色，才能在資料框架上呼叫。

當您在 .NET 中為 Apache Spark 的互動式體驗 (（例如 [Azure Synapse 筆記本](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks)) ）執行 udf 時，必須牢記一些重要事項。

## <a name="faqs"></a>常見問題集

1. **為什麼我的 UDF 參考自訂使用者定義物件會擲回錯誤 `Type Submission#_ is not marked as serializable` ？**  
    .NET Interactive 會使用資料格提交編號的包裝函式類別來包裝每個資料格，以唯一識別所提交的每個資料格。 現在依照 [本指南](udf-guide.md)中的詳細說明，當參考自訂物件的 UDF 序列化時，也會挑選其目標來進行序列化，在 .net Interactive 的情況下，會由定義自訂物件的資料格包裝函式類別來包裝。
   現在讓我們來看看這會如何影響我們在筆記本中的 UDF 定義：

    ![UDF 序列化錯誤](./media/dotnet-interactive/udf-serialization-error.png)

    如同在案例中所見 `udf2_fails` ，我們看到的錯誤訊息指出型別未 `Submission#7` 標示為可序列化，這是因為 .net Interactive 的運作方式是將資料格中所定義的每個物件，包裝在 `Submission#` 動態產生的類別中，因此不會標示為 `Serializable` ，因此會發生錯誤。
    基於這個理由， **參考其中的自訂物件的 UDF 必須定義在與該物件相同的資料格中**。

2. **為什麼廣播變數無法使用 .NET Interactive？**  
    基於上述原因，廣播變數不適用於 .NET Interactive。 最好是 [在廣播變數上進行這份指南](broadcast-guide.md) ，以深入瞭解廣播變數是什麼，以及如何使用它們。 廣播變數無法使用互動式案例的原因，是因為 .NET 互動的設計會附加儲存格所定義的每個物件，其中包含其資料格提交類別，因為它不會標示為可序列化，所以會因為先前所示的相同例外狀況而失敗。
   讓我們更深入瞭解下列範例：

    ![廣播變數失敗](./media/dotnet-interactive/broadcast-fails.png)

    如先前章節中的建議，我們會在此案例中定義 UDF 與其參考的物件 (廣播變數) 在相同的資料格中，但是仍 `SerializationException` 會看到錯誤抱怨 `Microsoft.Spark.Sql.Session` 未標示為可序列化。 這是因為當編譯器嘗試序列化廣播變數物件時 `bv` ，它會尋找其名稱，並將 [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) `spark` 它標示為可序列化的物件。 藉由查看此儲存格提交的反向組譯元件，可讓您更輕鬆地進行示範：

    ![反向組譯元件碼](./media/dotnet-interactive/decompiledAssembly.png)

    如果我們將此 [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) 類別標示為 `[Serializable]` ，我們可以讓它正常運作，但這並不是理想的解決方案，因為我們不想讓使用者能夠序列化 SparkSession 物件，因為這可能會導致一些非常奇怪的非預期行為。 這是已知的問題，並會在此 [進行追蹤，](https://github.com/dotnet/spark/issues/619) 並將在未來的版本中解決。
