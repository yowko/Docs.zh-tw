---
title: 運算式主體成員 - C# 程式設計指南
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826612"
---
# <a name="expression-bodied-members-c-programming-guide"></a>運算式主體成員 (C# 程式設計手冊)

運算式主體定義可讓您以極為簡潔且可讀的形式提供成員的實作。 只要任何所支援成員 (例如方法或屬性) 的邏輯包含單一運算式，就可以使用運算式主體定義。 運算式主體定義的一般語法如下︰

```csharp
member => expression;
```

其中 *expression* 是有效的運算式。

方法和唯讀屬性的運算式主體定義支援是在 C# 6 中引進，並在 C# 7.0 中擴充。 運算式主體定義可以與下表中所列的類型成員搭配使用︰

|成員  |支援作為... |
|---------|---------|
|[方法](#methods)  |C# 6 |
|[唯讀屬性](#read-only-properties)   |C# 6  |
|[Property](#properties)  |C# 7.0 |
|[建構函式](#constructors)   |C# 7.0 |
|[完成項](#finalizers)     |C# 7.0 |
|[索引子](#indexers)       |C# 7.0 |

## <a name="methods"></a>方法

運算式主體方法包含傳回型別符合方法傳回型別之值的單一運算式，或是傳回可執行某項作業之 `void` 的方法。 例如，覆寫 <xref:System.Object.ToString%2A> 方法的類型通常會包括可傳回目前物件之字串表示的單一運算式。

下列範例定義 `Person` 類別，以將 <xref:System.Object.ToString%2A> 方法覆寫為運算式主體定義。 它也會定義 `DisplayName` 方法，以向主控台顯示名稱。 請注意，`return` 關鍵字未用於 `ToString` 運算式主體定義中。

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

如需詳細資訊，請參閱[方法 (C# 程式設計手冊)](../classes-and-structs/methods.md)。

## <a name="read-only-properties"></a>唯讀屬性

從 C# 6 開始，您可以使用運算式主體定義來實作唯讀屬性。 若要這麼做，請使用下列語法：

```csharp
PropertyType PropertyName => expression;
```

下列範例會定義 `Location` 類別，其唯讀 `Name` 屬性會實作為可傳回私用 `locationName` 欄位值的運算式主體定義：

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

如需屬性的詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。

## <a name="properties"></a>屬性

從 C# 7.0 開始，您可以使用運算式主體定義來實作屬性 `get` 和 `set` 存取子。 下列範例示範如何進行這項操作：

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

如需屬性的詳細資訊，請參閱[屬性 (C# 程式設計手冊)](../classes-and-structs/properties.md)。

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

## <a name="indexers"></a>索引子

如同屬性，如果 get 存取子所包含的單一陳述式傳回值，或 set 存取子執行簡單指派，則索引子的 get 和 set 存取子會包含運算式主體定義。

下列範例會定義名為 `Sports` 的類別，這個類別包括內含數個運動名稱的內部 <xref:System.String> 陣列。 索引子的 get 和 set 存取子會實作為運算式主體定義。

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

如需詳細資訊，請參閱[索引子 (C# 程式設計手冊)](../indexers/index.md)。
