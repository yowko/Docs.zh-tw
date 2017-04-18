---
title: "如何：從 URL 擷取通訊協定和通訊埠編號 | Microsoft Docs"
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
  - ".NET Framework 規則運算式, 範例"
  - "使用規則運算式剖析文字, 範例"
  - "使用規則運算式的模式比對, 範例"
  - "規則運算式 [.NET Framework], 範例"
  - "規則運算式, 範例"
  - "使用規則運算式搜尋, 範例"
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：從 URL 擷取通訊協定和通訊埠編號
下列範例會從 URL 中擷取通訊協定和通訊埠編號。  
  
## 範例  
 此範例會使用 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> 方法來傳回通訊協定和通訊埠編號 \(中間以冒號隔開\)。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 規則運算式模式 `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` 可以如下表所示來解讀。  
  
|模式|說明|  
|--------|--------|  
|`^`|在字串開頭開始比對。|  
|`(?<proto>\w+)`|比對一個或多個文字字元。  將這個群組命名為 `proto`。|  
|`://`|比對冒號加兩個斜線符號。|  
|`[^/]+?`|比對一個或多個 \(但越少越好\) 出現的任何字元 \(但斜線符號除外\)。|  
|`(?<port>:\d+)?`|比對一個或多個出現的下列模式：冒號加一個或多個數字字元。  將這個群組命名為 `port`。|  
|`/`|比對斜線符號。|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> 方法會展開 `${proto}${port}` 取代序列，以將規則運算式模式中所擷取之兩個具名群組的值串連。  另一種方便的做法是將 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName> 屬性所傳回的集合物件中擷取的字串串連。  
  
 下列程式碼使用 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> 方法和兩個替代項目 \(`${proto}` 和 `${port}`\)，讓輸出字串包含擷取的群組。  您可以改為從相符項目的 <xref:System.Text.RegularExpressions.GroupCollection> 物件中擷取該群組，如下列程式碼所示。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## 請參閱  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)