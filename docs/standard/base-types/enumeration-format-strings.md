---
title: "列舉類型格式字串 | Microsoft Docs"
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
  - "列舉類型格式字串"
  - "格式規範, 列舉類型格式字串"
  - "格式化 [.NET Framework], 列舉"
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 列舉類型格式字串
您可以使用 <xref:System.Enum.ToString%2A?displayProperty=fullName> 方法來建立表示數值、十六進位或列舉型別成員之字串值的新字串物件。  這個方法接受列舉型別格式字串的其中之一來指定您想要傳回的值。  
  
 下表列出列舉型別格式字串和它們傳回的值。  這些格式規範不區分大小寫。  
  
|格式字串|結果|  
|----------|--------|  
|G 或 g|將列舉型別項目顯示為字串值，如果可能的話，否則顯示目前執行個體的整數值。  如果列舉型別因設定 **Flags** 屬性 \(Attribute\) 而被定義，各個有效項目的字串值都會以逗號分隔而串連在一起。  如果 **Flags** 屬性未設定，無效值將顯示為數值項目。  以下範例說明 G 格式規範。<br /><br /> [!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
 [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]|  
|F 或 f|將列舉型別項目顯示為字串值，如果可能的話。  如果值可以完整顯示為列舉型別中項目的總和 \(即使 **Flags** 屬性不出現\)，各個有效項目的字串值都會以逗號分隔而串連在一起。  如果值無法完全由列舉型別項目來決定，那麼這值便會格式化為整數值。  以下範例說明 F 格式規範。<br /><br /> [!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
 [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]|  
|D 或 d|以盡可能簡短的表示，將列舉型別項目顯示為整數值。  以下範例說明 D 格式規範。<br /><br /> [!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
 [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]|  
|X 或 x|將列舉型別項目顯示為十六進位值。  值以必要的前置零字元來表示，以確保這值最少有八位數長度。  以下範例說明 X 格式規範。<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
 [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]|  
  
## 範例  
 下列範例定義稱為 `Colors` 的列舉型別，它由三個項目組成：`Red`、`Blue` 和 `Green`。  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 列舉型別定義之後，可用下列方式來宣告執行個體。  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 然後 `Color.ToString(System.String)` 方法就可根據傳遞的格式規範，以不同方式顯示列舉值。  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## 請參閱  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)