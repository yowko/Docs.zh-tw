---
title: 運算式主體成員 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5690a2ddb9127bb0c9b06d3607e3d105fca9a2e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="expression-bodied-members-c-programming-guide"></a>運算式主體成員 (C# 程式設計手冊)
運算式主體定義可讓您以極為簡潔且可讀的形式提供成員的實作。 只要任何所支援成員 (例如方法或屬性) 的邏輯包含單一運算式，就可以使用運算式主體定義。 運算式主體定義的一般語法如下︰

```csharp
member => expression;
```

其中 *expression* 是有效的運算式。 

方法和屬性 get 存取子的運算式主體定義支援是在 C# 6 中引進，並在 C# 7.0 中擴充。 運算式主體定義可以與下表中所列的類型成員搭配使用︰ 

|成員  |支援作為... |
|---------|---------|
|[方法](#methods)  |C# 6 |
|[建構函式](#constructors)   |C# 7.0 |
|[完成項](#finalizers)     |C# 7.0 |
|[屬性 Get](#property-get-statements)  |C# 6 |
|[屬性 Set](#property-set-statements)  |C# 7.0 |
|[索引子](#indexers)       |C# 7.0 |

## <a name="methods"></a>方法

運算式主體方法包含傳回型別符合方法傳回型別之值的單一運算式，或是傳回可執行某項作業之 `void` 的方法。 例如，覆寫 <xref:System.Object.ToString%2A> 方法的類型通常會包括可傳回目前物件之字串表示的單一運算式。 

下列範例定義 `Person` 類別，以將 <xref:System.Object.ToString%2A> 方法覆寫為運算式主體定義。 它也會定義 `Show` 方法，以向主控台顯示名稱。 請注意，`return` 關鍵字未用於 `ToString` 運算式主體定義中。

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

如需詳細資訊，請參閱[方法 (C# 程式設計手冊)](../classes-and-structs/methods.md)。
 
## <a name="constructors"></a>建構函式

建構函式的運算式主體定義通常會包含單一指派運算式或方法呼叫，以處理建構函式的引數，或初始化執行個體狀態。 

下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。 運算式主體定義會將引數指派給 `Name` 屬性。

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

如需詳細資訊，請參閱[建構函式 (C# 程式設計手冊)](../classes-and-structs/constructors.md)。

## <a name="finalizers"></a>完成項

完成項的運算式主體定義通常包含清除陳述式，例如，發行不受管理資源的陳述式。

下列範例定義完成項，以使用運算式主體定義來指出已呼叫完成項。

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

如需詳細資訊，請參閱[完成項 (C# 程式設計手冊)](../classes-and-structs/destructors.md)。

## <a name="property-get-statements"></a>屬性 get 陳述式

如果您選擇自行實作屬性 get 存取子，則可以使用單一運算式的運算式主體定義，而單一運算式只會傳回屬性值。 請注意，不會使用 `return` 陳述式。

下列範例會定義 `Location.Name` 屬性，這個屬性的屬性 get 存取子會傳回支援這個屬性的私用 `locationName` 欄位值。 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

您可以實作使用運算式主體定義的唯讀屬性，而不需要明確 `set` 陳述式。 其語法為：

```csharp
PropertyName => returnValue;
```

下列範例會定義 `Location` 類別，這個類別的唯讀 `Name` 屬性實作為可傳回私用 `locationName` 欄位值的運算式主體定義。

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

如需詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。

## <a name="property-set-statements"></a>屬性 set 陳述式

如果您選擇自行實作屬性 set 存取子，則可以使用單行運算式的運算式主體定義，而單行運算式會將值指派給支援此屬性的欄位。

下列範例會定義 `Location.Name` 屬性，這個屬性的屬性 set 陳述式會將其輸入引數指派給支援這個屬性的私用 `locationName` 欄位。

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

如需詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。

## <a name="indexers"></a>索引子

如同屬性，如果 get 存取子所包含的單一陳述式傳回值，或 set 存取子執行簡單指派，則索引子的 get 和 set 存取子會包含運算式主體定義。

下列範例會定義名為 `Sports` 的類別，這個類別包括內含數個運動名稱的內部 <xref:System.String> 陣列。 索引子的 get 和 set 存取子會實作為運算式主體定義。

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

如需詳細資訊，請參閱[索引子 (C# 程式設計手冊)](../indexers/index.md)。

