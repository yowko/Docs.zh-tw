---
title: "修剪和移除從.NET 中的字串的字元"
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
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fde24a97234d275d3d599f13bfc4063af939507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>修剪和移除從.NET 中的字串的字元
如果您將句子剖析成個別文字，最後可能會得到許多文字，但文字任一端有空格 (也稱為空白字元)。 在這種情況下，您可以使用 **System.String** 類別中的其中一個 Trim 方法，從字串中的指定位置移除任意數目的空格或其他字元。 下表描述可用的 Trim 方法。  
  
|方法名稱|用法|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|將字元陣列中字串開頭和結尾指定的空格或空白字元移除。|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|從字串尾端移除字元陣列中指定的字元。|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|從字串開頭移除字元陣列中指定的字元。|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|從字串中指定的索引位置移除指定的字元數。|  
  
## <a name="trim"></a>Trim  
 您可以使用 <xref:System.String.Trim%2A?displayProperty=nameWithType> 方法，輕鬆地移除字串頭尾的空格，如下列範例所示。  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 您也可以將字元陣列中字串開頭和結尾指定的字元移除。 下列範例將會移除空白字元、句號和星號。  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd  
 **String.TrimEnd** 方法會從字串結尾移除字元，並建立新的字串物件。 系統會將字元陣列傳遞給這個方法，以指定要移除的字元。 字元陣列中的項目順序不會影響修剪作業。 一旦找到陣列中未指定的字元時，修剪作業就會停止。  
  
 下列範例會移除字串使用的最後一個字母**TrimEnd**方法。 在此範例中，`'r'` 字元和 `'W'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。 請注意，此程式碼會移除 `MyString` 的最後一個字以及第一個字的一部分。  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 此程式碼會讓主控台顯示 `He`。  
  
 下列範例會使用 **TrimEnd** 方法，移除字串的最後一個文字。 在這個程式碼中，`Hello` 文字後接一個逗號，不過由於要修剪的字元陣列中未指定逗號，因此修剪作業會在逗號處停止。  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 此程式碼會讓主控台顯示 `Hello,`。  
  
## <a name="trimstart"></a>TrimStart  
 **String.TrimStart** 方法與 **String.TrimEnd** 方法類似，只是它會移除現有字串物件開頭的字元以建立新字串。 系統會將字元陣列傳遞給 **TrimStart** 方法，以指定要移除的字元。 使用 **TrimEnd** 時，字元陣列中的項目順序不會影響修剪作業。 一旦找到陣列中未指定的字元時，修剪作業就會停止。  
  
 下列範例會移除字串的第一個文字。 在此範例中，`'l'` 字元和 `'H'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 此程式碼會讓主控台顯示 `World!`。  
  
## <a name="remove"></a>移除  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> 方法會從現有字串中的指定位置開始，移除指定的字元數。 這個方法會假設以零為起始的索引。  
  
 下列範例會於字串中以零為起始之索引的位置五開始，從字串中移除 10 個字元。  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 您也可以從字串中移除指定的字元或子字串，方法是呼叫 <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法並指定空字串 (<xref:System.String.Empty?displayProperty=nameWithType>) 做為取代。 下列範例將會從字串中移除所有逗號。  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>另請參閱  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)
