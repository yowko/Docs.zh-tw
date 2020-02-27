---
title: 介面中的索引子 - C# 程式設計指南
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627834"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>介面中的索引子 (C# 程式設計手冊)

索引子可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。 介面索引子的存取子在下列方面與[類別](../../language-reference/keywords/class.md)索引子的存取子不同：

- 介面存取子不會使用修飾詞。
- 介面存取子通常沒有主體。

存取子的目的是要指出索引子是讀寫、唯讀或僅寫入。 您可以為介面中定義的索引子提供實作為，但這很罕見。 索引子通常會定義用來存取資料欄位的 API，而且資料欄位不能在介面中定義。

介面索引子存取子的範例如下：

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

索引子的簽章必須與相同介面中所宣告之其他所有索引子的簽章不同。

## <a name="example"></a>範例

下列範例示範如何實作介面索引子。

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

在上述範例中，您可以使用介面成員的完整名稱來使用明確介面成員實作。 例如：

```csharp
string IIndexInterface.this[int index]
{
}
```

不過，類別實作具有相同索引子簽章的多個介面時，只需要完整名稱，即可避免模稜兩可。 例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有相同的索引子簽章，則需要明確介面成員實作。 也就是說，下列索引子宣告：

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

在 `ICitizen` 介面上實作索引子。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [索引子](./index.md)
- [屬性](../classes-and-structs/properties.md)
- [介面](../interfaces/index.md)
