---
title: "格式化數值結果表 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 16976f5a59bd4eb0eca29553aff87d4fe0b1d247
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a>格式化數值結果表 (C# 參考)
您可以使用 <xref:System.String.Format%2A?displayProperty=fullName> 方法，或透過會呼叫 `String.Format` 的 <xref:System.Console.Write%2A?displayProperty=fullName> 或 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 方法格式化數值結果。 使用格式字串來指定格式。 下表包含支援的標準格式字串。 格式字串的格式如下︰`Axx`，其中 `A` 是格式規範，而 `xx` 是有效位數規範。 格式規範控制套用到數值之格式的類型，而有效位數規範控制格式化輸出的有效位數或小數位數。 有效位數規範的值範圍是從 0 到 99。  
  
 如需標準和自訂格式字串的詳細資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。 如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=fullName>。  
  
|格式規範|描述|範例|輸出|  
|----------------------|-----------------|--------------|------------|  
|C 或 c|貨幣|Console.Write("{0:C}", 2.5);<br /><br /> Console.Write("{0:C}", -2.5);|$2.50<br /><br /> ($2.50)|  
|D 或 d|Decimal|Console.Write("{0:D5}", 25);|00025|  
|E 或 e|科學記號|Console.Write("{0:E}", 250000);|2.500000E+005|  
|F 或 f|固定點|Console.Write("{0:F2}", 25);<br /><br /> Console.Write("{0:F0}", 25);|25.00<br /><br /> 25|  
|G 或 g|一般|Console.Write("{0:G}", 2.5);|2.5|  
|N 或 n|數字|Console.Write("{0:N}", 2500000);|2,500,000.00|  
|X 或 x|十六進位|Console.Write("{0:X}", 250);<br /><br /> Console.Write("{0:X}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)   
 [類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [string](../../../csharp/language-reference/keywords/string.md)

