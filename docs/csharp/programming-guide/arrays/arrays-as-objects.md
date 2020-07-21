---
title: 將陣列當做物件 - C# 程式設計手冊
description: 'C # 中的陣列是抽象基底類型陣列的物件。 您可以使用陣列的屬性和其他類別成員，例如 Length 屬性。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474718"
---
# <a name="arrays-as-objects-c-programming-guide"></a>將陣列當做物件 (C# 程式設計手冊)

在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。 <xref:System.Array> 是所有陣列類型的抽象基底類型。 您可以使用具有的屬性和其他類別成員 <xref:System.Array> 。 其中一個範例是使用 <xref:System.Array.Length%2A> 屬性來取得陣列的長度。 下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。

## <a name="example"></a>範例

這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [陣列](./index.md)
- [一維陣列](./single-dimensional-arrays.md)
- [多維陣列](./multidimensional-arrays.md)
- [不規則陣列](./jagged-arrays.md)
