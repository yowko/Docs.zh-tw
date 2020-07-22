---
title: 介面屬性 - C# 程式設計手冊
description: '屬性可以在 c # 中的介面上宣告。 這個範例會宣告介面屬性存取子。'
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864965"
---
# <a name="interface-properties-c-programming-guide"></a>介面屬性 (C# 程式設計手冊)

屬性可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。 下列範例會宣告介面屬性存取子：

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

介面屬性通常不會有主體。 存取子會指出屬性為讀寫、唯讀或僅寫入。 不同于類別和結構，宣告不含主體的存取子並不會宣告[自動實作為屬性](auto-implemented-properties.md)。 從 c # 8.0 開始，介面可以定義成員的預設實值，包括屬性。 在介面中定義屬性的預設實為罕見，因為介面可能不會定義實例資料欄位。

## <a name="example"></a>範例

在此範例中，`IEmployee` 介面具有讀寫屬性 `Name` 和唯讀屬性 `Counter`。 `Employee` 類別會實作 `IEmployee` 介面，並使用這兩個屬性。 程式會讀取新員工的姓名和目前員工人數，並顯示員工姓名和計算的員工人數。

您可以使用屬性的完整名稱，而屬性參考在其中宣告成員的介面。 例如：

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

上述範例示範[明確的介面執行](../interfaces/explicit-interface-implementation.md)。 例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有 `Name` 屬性，則需要明確介面成員實作。 也就是說，下列屬性宣告：

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

在 `IEmployee` 介面上實作 `Name` 屬性，而下列宣告：

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

在 `ICitizen` 介面上實作 `Name` 屬性。

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>範例輸出

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [屬性](./properties.md)
- [使用屬性](./using-properties.md)
- [屬性與索引子之間的比較](../indexers/comparison-between-properties-and-indexers.md)
- [索引子](../indexers/index.md)
- [介面](../interfaces/index.md)
