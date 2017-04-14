---
title: "在 .NET Framework 中填補字串 | Microsoft Docs"
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
  - "填補字串"
  - "PadLeft 方法"
  - "PadRight 方法"
  - "字串 [.NET Framework], 填補"
  - "空白字元"
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 在 .NET Framework 中填補字串
使用下列其中一個 <xref:System.String> 方法可建立新的字串，該字串是由以前置或尾端字元填補至指定之總長度的原始字串所組成。  填補字元可以是空白字元或指定的字元，使其看起來為向右對齊或向左對齊。  
  
|方法名稱|使用|  
|----------|--------|  
|<xref:System.String.PadLeft%2A?displayProperty=fullName>|以前置字元填補至指定之總長度的字串。|  
|<xref:System.String.PadRight%2A?displayProperty=fullName>|以尾端字元填補至指定之總長度的字串。|  
  
## PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=fullName> 方法會建立新的字串，其方式是以足夠的前置填補字元串連到原始字串，使其達到指定的總長度。  <xref:System.String.PadLeft%28System.Int32%29?displayProperty=fullName> 方法會使用泛空白字元 \(White Space\) 做為填補字元，而 <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=fullName> 方法可讓您指定自己的填補字元。  
  
 下列程式碼範例會使用 <xref:System.String.PadLeft%2A> 方法建立長度為二十個字元的新字串。  範例中會將 "`--------Hello World!`" 顯示在主控台上。  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## PadRight  
 <xref:System.String.PadRight%2A?displayProperty=fullName> 方法會建立新的字串，其方式是以足夠的尾端填補字元串連到原始字串，使其達到指定的總長度。  <xref:System.String.PadRight%28System.Int32%29?displayProperty=fullName> 方法會使用泛空白字元 \(White Space\) 做為填補字元，而 <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=fullName> 方法可讓您指定自己的填補字元。  
  
 下列程式碼範例會使用 <xref:System.String.PadRight%2A> 方法來建立具有二十個字元長度的新字串，  範例中會將 "`Hello World!--------`" 顯示在主控台上。  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## 請參閱  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)