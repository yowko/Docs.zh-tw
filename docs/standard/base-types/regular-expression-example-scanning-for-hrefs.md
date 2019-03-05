---
title: 規則運算式範例：掃描 HREF
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e743f32637a7e15b4b017bbe30aa02ad8388fbe
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975962"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>規則運算式範例：掃描 HREF
下列範例將搜尋輸入字串，並顯示所有 href="..." 值和它們在字串中的位置。  
  
## <a name="the-regex-object"></a>Regex 物件  
 由於可從使用者程式碼多次呼叫 `DumpHRefs` 方法，因此它會使用 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法。 這可讓規則運算式引擎快取規則運算式，並避免在每次呼叫方法時因將新 <xref:System.Text.RegularExpressions.Regex> 物件具現化而導致的額外負荷。 接著會使用 <xref:System.Text.RegularExpressions.Match> 物件逐一查看字串中的所有相符項目。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 下列範例說明如何呼叫 `DumpHRefs` 方法。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 規則運算式模式 `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` 的解譯方式如下表所示。  
  
|模式|說明|  
|-------------|-----------------|  
|`href`|比對常值字串 "href"。 該比對不區分大小寫。|  
|`\s*`|比對零個以上的空白字元。|  
|`=`|比對等號。|  
|`\s*`|比對零個以上的空白字元。|  
|`(?:\["'\](?<1>\[^"'\]*)["']|(?<1>\S+))`|比對下列其中一項，而不將結果指派給擷取的群組：<br /> <ul><li><p>引號 (或單引號)，後面加上零個或多個引號 (或單引號) 以外的任何字元，再加上引號 (或單引號)。 此模式中包含名為 `1` 的群組。</p></li><li><p>一個或多個非空白字元。 此模式中包含名為 `1` 的群組。</p></li></ul>|  
|`(?<1>[^"']*)`|將零個或多個引號 (或單引號) 以外的任何字元指派給名為 `1` 的擷取端群組。|  
|`(?<1>\S+)`|將一或多個非空白字元指派給名為 `1` 的擷取群組。|  
  
## <a name="match-result-class"></a>比對結果類別  
 搜尋的結果會儲存在 <xref:System.Text.RegularExpressions.Match> 類別中，可讓您存取搜尋擷取的所有子字串。 它也會記住要搜尋的字串與所用的規則運算式，使其能呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> 方法，從最後一個搜尋結束的位置開始執行其他搜尋。  
  
## <a name="explicitly-named-captures"></a>明確命名的擷取  
 在傳統的規則運算式中，會自動將擷取括號依序編號。 這會導致兩個問題。 第一，如果修改規則運算式時，是以插入或移除一組括號來進行，就必須重新撰寫所有參考已編號擷取的程式碼，以反映新的編號。 第二，不同的括號通常用來提供兩個替代運算式以進行可接受的比對，因此可能難以判斷這兩個運算式是哪一個實際傳回結果。  
  
 為了解決這些問題，<xref:System.Text.RegularExpressions.Regex> 類別支援 `(?<name>…)` 的語法，可將相符項目擷取至指定的位置 (該位置可以使用字串或整數命名；重新叫用整數的速度更快)。 因此，相同字串的所有替代比對皆可導向相同的位置。 萬一發生衝突時，最後一個進入位置的比對就是成功的比對 (不過，您可以使用單一位置之多個比對的完整清單。 如需詳細資訊，請參閱 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 集合。)  
  
## <a name="see-also"></a>另請參閱

- [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)
