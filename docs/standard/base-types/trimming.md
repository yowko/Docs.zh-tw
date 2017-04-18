---
title: "在 .NET Framework 中從字串中修剪和移除字元 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Remove 方法"
  - "移除字元"
  - "字串 [.NET Framework], 移除字元"
  - "Trim 方法"
  - "TrimEnd 方法"
  - "修剪字元"
  - "TrimStart 方法"
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 在 .NET Framework 中從字串中修剪和移除字元
如果您正在將句子剖析為個別的單字，結果可能會在單字的前面或後面出現空格 \(也稱為空白字元\)。  在這種情況下，您可以使用 **System.String** 類別的其中一個修剪方法，將字串中指定位置的任意個空格或其他字元移除。  下表會描述可用的修剪方法。  
  
|方法名稱|使用|  
|----------|--------|  
|<xref:System.String.Trim%2A?displayProperty=fullName>|將陣列開頭或結尾的空白字元或特定字元移除。|  
|<xref:System.String.TrimEnd%2A?displayProperty=fullName>|從字串結尾移除字元陣列中指定的字元|  
|<xref:System.String.TrimStart%2A?displayProperty=fullName>|從字串開頭移除字元陣列中指定的字元|  
|<xref:System.String.Remove%2A?displayProperty=fullName>|從字串中的指定索引位置移除指定的字元數|  
  
## Trim  
 您可以使用 <xref:System.String.Trim%2A?displayProperty=fullName>方法，輕鬆地移除字串頭尾的空白字元，如下列程式碼範例所示。  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 您也可以移除在字元陣列頭尾的字元。  下列範例會移除空白字元、句號和星號。  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## TrimEnd  
 **String.TrimEnd** 方法會移除字串結尾的字元，建立新的字串物件。  字元陣列會傳遞至這個方法，用來指定要移除的字元。  字元陣列中的元素順序不會影響修剪作業。  如果找到陣列中未指定的字元，修剪便會停止。  
  
 下列範例會使用 **TrimEnd** 方法移除字串的最後幾個字母。  在這個範例中，會將 `'r'` 字元和 `'W'` 字元的位置顛倒，以便說明陣列中的字元順序並沒有影響。  請注意，這個程式碼會移除 `MyString` 的最後一個字和第一個字的一部分。  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 這個程式碼會將 `He` 顯示在主控台上。  
  
 下列範例會使用 **TrimEnd** 方法移除字串的最後一個字。  在這個程式碼中，`Hello` 這個字的後面接著一個逗號，而且在要修剪的字元陣列中並未指定逗號，因此修剪到逗號時便會停止。  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 這個程式碼會將 `Hello,` 顯示在主控台上。  
  
## TrimStart  
 **String.TrimStart** 方法和 **String.TrimEnd** 方法類似，只不過它是藉由移除現有字串物件開頭的字元來建立新的字串。  字元陣列會傳遞至 **TrimStart** 方法，用來指定要移除的字元。  和 **TrimEnd** 方法一樣，字元陣列中的元素順序不會影響修剪作業。  如果找到陣列中未指定的字元，修剪便會停止。  
  
 下列範例會移除字串的第一個字。  在這個範例中，會將 `'l'` 字元和 `'H'` 字元的位置顛倒，以便說明陣列中的字元順序並沒有影響。  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 這個程式碼會將 `World!` 顯示在主控台上。  
  
## 移除  
 <xref:System.String.Remove%2A?displayProperty=fullName> 方法會從現有字串中的指定位置開始，移除指定的字元數。  這個方法會採用以零起始的索引。  
  
 下列範例會從字串中以零起始索引的第五個位置開始，移除其中的十個字元。  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 您可以從字串中移除指定的字元或子字串藉由呼叫 <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=fullName> 方法和指定空字串 \(<xref:System.String.Empty?displayProperty=fullName>做為取代。  下列範例會從字串移除所有逗號。  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## 請參閱  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)