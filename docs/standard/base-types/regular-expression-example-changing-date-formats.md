---
title: "規則運算式範例：變更日期格式 | Microsoft Docs"
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
  - "使用規則運算式搜尋，範例"
  - "使用規則運算式剖析文字，範例"
  - "規則運算式，範例"
  - ".NET Framework 規則運算式，範例"
  - "規則運算式 [.NET Framework]，範例"
  - "使用規則運算式的模式比對，範例"
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# 規則運算式範例：變更日期格式
下列程式碼範例會使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> 方法，將具有 *mm*\/*dd*\/*yy* 格式的日期取代成具有 *dd*\-*mm*\-*yy* 格式的日期。  
  
## 範例  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 以下程式碼將說明如何在應用程式中呼叫 `MDYToDMY` 方法。  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## 註解  
 規則運算式模式 `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` 的解譯方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|開始字緣比對。|  
|`(?<month>\d{1,2})`|比對一個或兩個十進位數字。  這是 `month` 擷取群組。|  
|`/`|比對斜線符號。|  
|`(?<day>\d{1,2})`|比對一個或兩個十進位數字。  這是 `day` 擷取群組。|  
|`/`|比對斜線符號。|  
|`(?<year>\d{2,4})`|比對二到四個十進位數字。  這是 `year` 擷取群組。|  
|`\b`|結束字緣比對。|  
  
 模式 `${day}-${month}-${year}` 會定義取代字串，如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`$(day)`|加入 `day` 擷取群組所擷取的字串。|  
|`-`|加入連字號。|  
|`$(month)`|加入 `month` 擷取群組所擷取的字串。|  
|`-`|加入連字號。|  
|`$(year)`|加入 `year` 擷取群組所擷取的字串。|  
  
## 請參閱  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)