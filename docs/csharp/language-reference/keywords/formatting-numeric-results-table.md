---
title: "格式化數值結果表 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "格式化 [C#]"
  - "數值格式化 [C#]"
  - "String.Format 方法"
  - "Console.Write 方法"
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 格式化數值結果表 (C# 參考)
如果要格式化數值結果，您可以使用 <xref:System.String.Format%2A?displayProperty=fullName> 方法，或者透過會呼叫 `String.Format` 的 <xref:System.Console.Write%2A?displayProperty=fullName> 或 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 方法。  此格式是以格式字串 \(Format String\) 指定。  下表包含支援的標準格式字串。  格式字串會使用下列格式：`Axx`，其中 `A` 是格式規範而 `xx` 是精確度規範。  格式規範控制了套用在數值上的格式類型，而精確度規範則控制格式化輸出的有效數字或小數位數的數目。  精確度規範的值範圍從 0 到 99。  
  
 如需標準和自訂格式字串的詳細資訊，請參閱 [格式化類型](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)。  如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=fullName>。  
  
|格式規範|描述|範例|Output|  
|----------|--------|--------|------------|  
|C 或 c|貨幣|Console.Write\("{0:C}", 2.5\);<br /><br /> Console.Write\("{0:C}", \-2.5\);|$2.50<br /><br /> \($2.50\)|  
|D 或 d|Decimal|Console.Write\("{0:D5}", 25\);|00025|  
|E 或 e|科學記號|Console.Write\("{0:E}", 250000\);|2.500000E\+005|  
|F 或 f|固定點|Console.Write\("{0:F2}", 25\);<br /><br /> Console.Write\("{0:F0}", 25\);|25.00<br /><br /> 25|  
|G 或 g|一般|Console.Write\("{0:G}", 2.5\);|2.5|  
|N 或 n|數字|Console.Write\("{0:N}", 2500000\);|2,500,000.00|  
|X 或 x|十六進位|Console.Write\("{0:X}", 250\);<br /><br /> Console.Write\("{0:X}", 0xffff\);|FA<br /><br /> FFFF|  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [標準數值格式字串](../Topic/Standard%20Numeric%20Format%20Strings.md)   
 [類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [字串](../../../csharp/language-reference/keywords/string.md)