---
title: 支援 LINQ 的 C# 功能
description: '瞭解搭配 LINQ 查詢和其他內容使用的 c # 功能。 這些語言結構是在 c # 3.0 中引進。'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 13254c69193e04ffcf11e3e23f1deb460063a6c1
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063688"
---
# <a name="c-features-that-support-linq"></a>支援 LINQ 的 C# 功能

下節將介紹 C# 3.0 中引進的新語言建構。 雖然這些新功能全都適用于 LINQ 查詢的程度，但它們並不限於 LINQ，而且可以在任何您覺得有用的內容中使用。

## <a name="query-expressions"></a>查詢運算式

查詢運算式使用類似 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。 在編譯時期，查詢語法會轉換成 LINQ 提供者的標準查詢運算子擴充方法的實作為方法呼叫。 應用程式使用 `using` 指示詞來指定適當的命名空間，藉此控制範圍內的標準查詢運算子。 下列查詢運算式會擷取字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../linq/index.md)。

## <a name="implicitly-typed-variables-var"></a>隱含型別變數 (var)

除了在宣告和初始化變數時明確指定類型，您還可以使用 [var](../../../language-reference/keywords/var.md) 修飾詞，指示編譯器推斷並指派類型，如下所示：

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

宣告為的變數，與 `var` 您明確指定類型的變數一樣強型別。 `var` 可用來建立匿名型別，但僅可用於區域變數。 陣列也可以使用隱含型別進行宣告。

如需詳細資訊，請參閱[隱含型別區域變數](../../classes-and-structs/implicitly-typed-local-variables.md)。

## <a name="object-and-collection-initializers"></a>物件和集合初始設定式

物件和集合初始設定式可以初始化物件，而不需要明確呼叫物件的建構函式。 初始設定式通常會用於將來源資料投影為新資料類型的查詢運算式中。 假設有個名為 `Customer` 的類別具有公用的 `Name` 和 `Phone` 屬性，則可如下列程式碼所示使用物件初始設定式：

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

延續我們的 `Customer` 類別，假設有一個稱為 `IncomingOrders` 的資料來源，而其每個訂單都有大型的 `OrderSize`，我們想要根據該訂單建立新的 `Customer`。 您可以針對此資料來源執行 LINQ 查詢，並使用物件初始化來填滿集合：

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

資料來源底下可能有比 `Customer` 類別更多的屬性 (例如 `OrderSize`)，但使用物件初始化時，從查詢傳回的資料會塑造為我們想要的資料型別；我們選擇與我們的類別相關的資料。 因此，我們現在有使用新的 `Customer` 填滿的 `IEnumerable`，這正是我們所需要的。 上述內容也可以使用 LINQ 的方法語法撰寫：

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

如需詳細資訊，請參閱

- [物件和集合初始設定式](../../classes-and-structs/object-and-collection-initializers.md)

- [標準查詢運算子的查詢運算式語法](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>匿名類型

匿名型別是由編譯器所建構，只有編譯器才知道類型名稱。 匿名型別提供了一個便利的方法，暫時將查詢結果中的一組屬性分組，而不需要另外定義具名類型。 匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

如需詳細資訊，請參閱[匿名](../../classes-and-structs/anonymous-types.md)型別。

## <a name="extension-methods"></a>擴充方法

擴充方法是一種可以與類型相關聯的靜態方法，因此可以像呼叫類型上的執行個體方法一樣呼叫它。 這項功能實際上可讓您「新增」方法至現有的類型，而不需要實際修改這些類型。 標準查詢運算子是一組擴充方法，可為任何可執行檔型別提供 LINQ 查詢功能 <xref:System.Collections.Generic.IEnumerable%601> 。

如需詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。

## <a name="lambda-expressions"></a>Lambda 運算式

Lambda 運算式是一種內嵌函式，其使用 => 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換成委派或運算式樹狀架構。 在 LINQ 程式設計中，當您對標準查詢運算子進行直接方法呼叫時，將會遇到 lambda 運算式。

如需詳細資訊，請參閱

- [匿名函式](../../statements-expressions-operators/anonymous-functions.md)

- [Lambda 運算式](../../../language-reference/operators/lambda-expressions.md)

- [運算式樹狀架構 (C#)](../expression-trees/index.md)

## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) (C#)](./index.md)
