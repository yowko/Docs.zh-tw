---
title: 在 .NET 中建立使用者定義函式 (UDF) 以進行 Apache Spark
description: 瞭解如何在適用于 Apache Spark 應用程式的 .NET 中，將使用者定義函數 (UDF) 。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 769bcf0a912d27e191dad82138648d1aefb3c3b6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955032"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>在 .NET 中建立使用者定義函式 (UDF) 以進行 Apache Spark

在本文中，您將瞭解如何在 .NET 中使用 (UDF) 的使用者定義函數來進行 Apache Spark。 [Udf) ](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) 是一種 Spark 功能，可讓您使用自訂功能來擴充系統的內建功能。 Udf 會從資料表內的單一資料列轉換值，以根據 UDF 中定義的邏輯，為每個資料列產生單一對應的輸出值。

## <a name="define-udfs"></a>定義 Udf

檢查下列 UDF 定義：

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

UDF 會以 `string` [資料框架](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) 資料[行](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14)的形式取得輸入，並傳回 `string` `hello` 附加在輸入前面的。

下列資料框架 `df` 包含名稱清單：

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

現在讓我們將上述定義的 `udf` 內容套用至資料框架 `df` ：

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

下列資料框架 `udfResult` 是 UDF 的結果：

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

若要進一步瞭解如何執行 Udf，請參閱 GitHub 上的 [UDF helper](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) 函式和 [範例](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) 。

## <a name="udf-serialization"></a>UDF 序列化

因為 Udf 是需要在背景工作角色上執行的函式，所以必須將它們序列化並傳送給背景工作角色，以作為來自驅動程式的承載一部分。 [委派](../../csharp/programming-guide/delegates/index.md)（即方法的參考）必須序列化及其[目標](xref:System.Delegate.Target%2A)，也就是目前的委派叫用實例方法的類別實例。 請參閱 [GitHub 中](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) 的此程式碼範例，以進一步瞭解 UDF 序列化的完成方式。

適用于 Apache Spark 的 .NET 使用 .NET Core，不支援序列化委派。 取而代之的是，會使用反映來序列化定義委派的目標。 當在通用範圍中定義多個委派時，它們會有一個共用的關閉，以成為要進行序列化之反映的目標。

### <a name="serialization-example"></a>序列化範例

下列程式碼片段會定義兩個函式委派中所參考的兩個字串變數，以傳回個別字串作為結果：

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

上述 c # 程式碼會產生下列 c # 反組解碼 (信用來源：從編譯器 [sharplab.io](https://sharplab.io)) 程式碼：

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

`func`和 `func2` 共用相同的結束 `<>c__DisplayClass0_0` ，也就是序列化委派和時序列化的目標 `func` `func2` 。 即使 `Func<string, string> a` 只有參考 `s1` ， `s2` 當位元組傳送給背景工作時也會序列化。

這可能會導致執行時間發生一些非預期的行為 (例如，在使用 [廣播變數](broadcast-guide.md)) 的情況下，我們建議您將函式中所使用之變數的可見度限制在該函式的範圍內。

下列程式碼片段是執行所需序列化行為的建議方法：

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

上述 c # 程式碼會產生下列 c # 反組解碼 (信用來源：從編譯器 [sharplab.io](https://sharplab.io)) 程式碼：

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

請注意， `func` 並 `func2` 不會再共用一則關閉，而且它們各自有個別的封閉 `<>c__DisplayClass0_0` `<>c__DisplayClass0_1` 。 當做序列化的目標使用時，參考的變數以外的任何專案都會被序列化為委派。 在常見的範圍中執行多個 Udf 時，請務必記住這項行為。

## <a name="some-spark-udf-caveats"></a>某些 Spark UDF 注意事項

* Udf 中的 Null 值可能會擲回例外狀況。 開發人員必須負責處理這些問題。
* Udf 不會利用 Spark 內建函數所提供的優化功能，因此建議您盡可能使用內建函數。

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯](debug.md)
