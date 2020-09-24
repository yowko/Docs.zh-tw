---
title: 泛型和陣列 - C# 程式設計指南
description: '瞭解 c # 程式設計中的泛型和陣列。 請參閱程式碼範例，並檢視其他可用的資源。'
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 808e9ddafea9806a74ccd105c8850e7b77b563be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151450"
---
# <a name="generics-and-arrays-c-programming-guide"></a>泛型和陣列 (C# 程式設計手冊)

在 C# 2.0 及更新版本中，下限為零的一維陣列會自動實作 <xref:System.Collections.Generic.IList%601>。 這能讓您建立泛型方法，使用相同的程式碼逐一查看陣列和其他集合類型。 這項技術主要用於讀取集合的資料。 <xref:System.Collections.Generic.IList%601> 介面不能用來新增或移除陣列中的元素。 如果您嘗試呼叫 <xref:System.Collections.Generic.IList%601> 方法，例如此內容陣列上的 <xref:System.Collections.Generic.IList%601.RemoveAt%2A>，會擲回例外狀況。  
  
 下列程式碼範例示範使用 <xref:System.Collections.Generic.IList%601> 輸入參數的單一泛型方法，如何逐一查看清單和陣列，本例中為整數陣列。  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic>
- [C # 程式設計指南](../index.md)
- [泛型](./index.md)
- [陣列](../arrays/index.md)
- [泛型](../../../standard/generics/index.md)
