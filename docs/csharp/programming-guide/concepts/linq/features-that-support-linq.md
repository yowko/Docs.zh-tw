---
title: 支援 LINQ 的 C# 功能
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 1029d34ae8823fe91c7e4bc92e168fcc1061c707
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594410"
---
# <a name="c-features-that-support-linq"></a>支援 LINQ 的 C# 功能

下節將介紹 C# 3.0 中引進的新語言建構。 雖然這些新功能或多或少都會用於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，但不限於 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，還可用於任何您認為實用的內容中。

## <a name="query-expressions"></a>查詢運算式

查詢運算式使用類似 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。 在編譯時期，查詢語法會轉換成對 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者實作的標準查詢運算子擴充方法進行的方法呼叫。 應用程式使用 `using` 指示詞來指定適當的命名空間，藉此控制範圍內的標準查詢運算子。 下列查詢運算式會擷取字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

如需詳細資訊，請參閱 [LINQ 查詢運算式](../../linq-query-expressions/index.md)。

## <a name="implicitly-typed-variables-var"></a>隱含型別變數 (var)

除了在宣告和初始化變數時明確指定類型，您還可以使用 [var](../../../language-reference/keywords/var.md) 修飾詞，指示編譯器推斷並指派類型，如下所示：

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

宣告為 `var` 的變數和明確指定類型的變數一樣具有強型別。 `var` 可用來建立匿名型別，但僅可用於區域變數。 陣列也可以使用隱含型別進行宣告。

如需詳細資訊，請參閱[隱含類型區域變數](../../classes-and-structs/implicitly-typed-local-variables.md)。

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

如需詳細資訊，請參閱:

- [物件和集合初始設定式](../../classes-and-structs/object-and-collection-initializers.md)

- [標準查詢運算子的查詢運算式語法](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>匿名類型

匿名型別是由編譯器所建構，只有編譯器才知道類型名稱。 匿名型別提供了一個便利的方法，暫時將查詢結果中的一組屬性分組，而不需要另外定義具名類型。 匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

如需詳細資訊，請參閱[匿名型別](../../classes-and-structs/anonymous-types.md)。

## <a name="extension-methods"></a>擴充方法

擴充方法是一種可以與類型相關聯的靜態方法，因此可以像呼叫類型上的執行個體方法一樣呼叫它。 這項功能實際上可讓您「新增」方法至現有的類型，而不需要實際修改這些類型。 標準查詢運算子是一組擴充方法，可為實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何類型提供 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢功能。

如需詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。

## <a name="lambda-expressions"></a>Lambda 運算式

Lambda 運算式是一種內嵌函式，其使用 => 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換成委派或運算式樹狀架構。 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 程式設計中，當您直接對標準查詢運算子進行方法呼叫時，就會遇到 Lambda 運算式。

如需詳細資訊，請參閱:

- [匿名函式](../../statements-expressions-operators/anonymous-functions.md)

- [Lambda 運算式](../../statements-expressions-operators/lambda-expressions.md)

- [運算式樹狀結構 (C#)](../expression-trees/index.md)

## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) (C#)](./index.md)
