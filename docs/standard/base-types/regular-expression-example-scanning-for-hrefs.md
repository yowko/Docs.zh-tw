---
title: "規則運算式範例：掃描 HREF | Microsoft Docs"
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
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# 規則運算式範例：掃描 HREF
下列範例會搜尋輸入字串，並顯示所有 href\="..." 值和它們在字串中的位置。  
  
## Regex 物件  
 `DumpHRefs` 方法由於可能會由使用者程式碼呼叫多次，因此它使用的是 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> 方法。  這可讓規則運算式引擎快取規則運算式，並避免每次呼叫方法就必須具現化新 <xref:System.Text.RegularExpressions.Regex> 物件的額外負荷。  接著會使用 <xref:System.Text.RegularExpressions.Match> 物件來逐一查看字串中的所有符合項目。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 下列範例會示範如何呼叫 `DumpHRefs` 方法。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 規則運算式模式 `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` 的解譯方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`href`|比對常值字串 "href"。  比對不區分大小寫。|  
|`\s*`|比對零個以上的空白字元。|  
|`=`|比對等號。|  
|`\s*`|比對零個以上的空白字元。|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|比對下列其中一項，但不將結果指派給擷取的群組：<br /><br /> -   引號\(或單引號\)，加上零個以上除引號外的其他任何字元，再加上引號\(或單引號\)。  名稱為 `1` 的群組包含在這個模式中。<br />-   一個或多個非空白字元。  名稱為 `1` 的群組包含在這個模式中。|  
|`(?<1>[^"']*)`|將零個以上除引號\(或單引號\)外的其他任何字元指派給名稱為 `1` 的擷取端群組。|  
|`"(?<1>\S+)`|將一個或多個非空白字元指派給名稱為 `1` 的擷取端群組。|  
  
## 比對結果類別  
 搜尋結果會儲存在 <xref:System.Text.RegularExpressions.Match> 類別中，這個類別可用於存取搜尋所擷取的全部子字串。  它也會記憶正在搜尋的字串和正在使用的規則運算式，所以可以呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法，自上次搜尋結束的地方開始執行另一個搜尋。  
  
## 明確命名的擷取  
 在傳統規則運算式中，擷取括號會自動循序編號。  這會導致兩個問題。  首先，如果用插入或移除一組括號的方式修改規則運算式，必須重新撰寫所有參考到已編號擷取的程式碼，才能反映新的編號。  其次，因為不同組的括號經常是用來提供兩個替代運算式給可接受的比對項目，因此要判斷哪一個替代運算式實際傳回結果，可能很困難。  
  
 為了解決這些問題，<xref:System.Text.RegularExpressions.Regex> 類別支援使用 `(?<name>…)` 的語法，將符合項目擷取至指定的位置 \(這個位置可以使用字串或整數來命名，而整數可以更快地重新叫用\)。  如此，相同字串的替代比對全都可以導向至相同位置。  如果發生衝突，落入位置的最後比對為成功的比對 \(不過，有單一位置的多個比對的完整清單可供使用。  如需詳細資訊，請參閱 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=fullName> 集合\)。  
  
## 請參閱  
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)