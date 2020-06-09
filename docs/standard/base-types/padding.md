---
title: 在 .NET 中填補字串
description: 瞭解如何在 .NET 中填補字串。 使用 PadLeft 和 PadRight 方法來加入開頭或尾端字元，以達到指定的總長度。
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 5bf7023a3429e932a44ad0a0bd3409012f77cbf9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594526"
---
# <a name="padding-strings-in-net"></a>在 .NET 中填補字串

使用下列其中一個 <xref:System.String> 方法來建立由原始字串組成的新字串，而原始字串會使用前置或後置字元填補至指定的總長度。 填補字元可為空白或指定的字元。 產生的字串會靠右或靠左顯示。 若原始字串的長度已經大於或等於需要的總長度，則填補方法會傳回原封不動的原始字串。如需詳細資訊，請參閱 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> 與 <xref:System.String.PadRight%2A?displayProperty=nameWithType> 這兩個多載方法的**傳回**一節。
  
|方法名稱|使用|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|以指定總長度的前置字元填補字串。|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|以指定總長度的後置字元填補字串。|  
  
## <a name="padleft"></a>PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> 方法會將足夠的前置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。 <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。  
  
 下列程式碼範例會使用 <xref:System.String.PadLeft%2A> 方法來建立長度為 20 個字元的新字串。 此範例會在主控台顯示 "`--------Hello World!`"。  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> 方法會將足夠的後置填補字元串連到原始字串，以達到指定的總長度，藉以建立新的字串。 <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> 方法會使用空白字元作為填補字元，而 <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> 方法可讓您指定自己的填補字元。  
  
 下列程式碼範例會使用 <xref:System.String.PadRight%2A> 方法來建立長度為 20 個字元的新字串。 此範例會在主控台顯示 "`Hello World!--------`"。  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>請參閱

- [基底字元串作業](basic-string-operations.md)
