---
title: "如何：從字串中刪除無效的字元 | Microsoft Docs"
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
  - "規則運算式、範例"
  - "清除輸入"
  - "使用者輸入、範例"
  - ".NET Framework 規則運算式、範例"
  - "規則運算式 [.NET Framework]、範例"
  - "Regex.Replace 方法"
  - "刪除無效的字元"
  - "Replace 方法"
  - "驗證使用者輸入"
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：從字串中刪除無效的字元
下列範例使用靜態 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> 方法將字串中無效的字元刪除。  
  
## 範例  
 您可以使用這個範例中定義的 `CleanInput` 方法來刪除已經輸入到接受使用者輸入之文字欄位中的潛在危害字元。  在此案例中，`CleanInput` 會刪除所有非英數字元 \(但句號 \(.\)、@ 符號和連字號 \(\-\) 除外\)，並且傳回其餘字串。  不過，您可以修改規則運算式模式，使其刪除不應包含在輸入字串中的任何字元。  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 規則運算式模式 `[^\w\.@-]` 會比對任何非文字字元、句號、@ 符號或連字號的字元。  文字字元是指任何字母、十進位數字或標點符號連接，例如底線。  符合這個模式的任何字元都會由 <xref:System.String.Empty?displayProperty=fullName> 取代，而這是取代模式所定義的字串。  若要允許在使用者輸入中採用其他字元，請將這些字元加入至規則運算式模式中的字元類別。  例如，規則運算式模式 `[^\w\.@-\\%]` 也允許在輸入字串中使用百分比符號和反斜線。  
  
## 請參閱  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)