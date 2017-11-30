---
title: "在.NET 中填補字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a>在.NET 中填補字串
使用下列其中一種<xref:System.String>方法來建立新的字串開頭或結尾指定的總長度的字元填補的原始字串所組成。 填補字元可以是空格或指定的字元，最後要靠右或靠左對齊。  
  
|方法名稱|用法|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|以指定總長度的前置字元填補字串。|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|以指定總長度的後置字元填補字串。|  
  
## <a name="padleft"></a>PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType>方法會建立新的字串串連到原始的字串，以便達到指定的總長度足夠前置填補字元。 <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>方法會使用做為填補字元的空白字元和<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>方法可讓您指定的填補字元。  
  
 下列程式碼範例使用<xref:System.String.PadLeft%2A>方法來建立新的字串長度的 20 個字元。 此範例會在主控台顯示 "`--------Hello World!`"。  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType>方法會建立新的字串串連到原始的字串，以便達到指定的總長度足夠尾端填補字元。 <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>方法會使用做為填補字元的空白字元和<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>方法可讓您指定的填補字元。  
  
 下列程式碼範例使用<xref:System.String.PadRight%2A>方法來建立新的字串長度的 20 個字元。 此範例會在主控台顯示 "`Hello World!--------`"。  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)
