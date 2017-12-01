---
title: "規則運算式範例：掃描 HREF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>規則運算式範例：掃描 HREF
下列範例將搜尋輸入字串，並顯示所有 href="..." 值和它們在字串中的位置。  
  
## <a name="the-regex-object"></a>Regex 物件  
 因為`DumpHRefs`方法可以從使用者程式碼呼叫多次，它會使用`static`(`Shared`在 Visual Basic 中)<xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>方法。 這可讓規則運算式引擎快取的規則運算式，並避免具現化新的額外負荷<xref:System.Text.RegularExpressions.Regex>物件每次呼叫該方法。 A<xref:System.Text.RegularExpressions.Match>物件會被用來逐一查看字串中的所有相符項目。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 下列範例說明如何呼叫 `DumpHRefs` 方法。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 規則運算式模式 `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` 的解譯方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`href`|比對常值字串 "href"。 該比對不區分大小寫。|  
|`\s*`|比對零個以上的空白字元。|  
|`=`|比對等號。|  
|`\s*`|比對零個以上的空白字元。|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|而不將結果指派給擷取群組符合下列其中一項：<br /><br /> -A 引號 （或單引號），後面接著零或多個引號 （或單引號），後面的引號 （或單引號） 以外的任何字元。 此模式中包含名為 `1` 的群組。<br />-一或多個非空格字元。 此模式中包含名為 `1` 的群組。|  
|`(?<1>[^"']*)`|將零個或多個引號 (或單引號) 以外的任何字元指派給名為 `1` 的擷取端群組。|  
|`"(?<1>\S+)`|將一或多個非空白字元指派給名為 `1` 的擷取群組。|  
  
## <a name="match-result-class"></a>比對結果類別  
 搜尋的結果會儲存在<xref:System.Text.RegularExpressions.Match>類別，可提供存取搜尋所擷取的子字串。 它也會記住要搜尋的字串和規則運算式使用，使其能呼叫<xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>方法，以執行另一個搜尋開始的最後一個結束的位置。  
  
## <a name="explicitly-named-captures"></a>明確命名的擷取  
 在傳統的規則運算式中，會自動將擷取括號依序編號。 這會導致兩個問題。 第一，如果修改規則運算式時，是以插入或移除一組括號來進行，就必須重新撰寫所有參考已編號擷取的程式碼，以反映新的編號。 第二，不同的括號通常用來提供兩個替代運算式以進行可接受的比對，因此可能難以判斷這兩個運算式是哪一個實際傳回結果。  
  
 若要解決這些問題，<xref:System.Text.RegularExpressions.Regex>類別支援的語法`(?<name>…)`至指定位置擷取相符項目 （可以使用字串或整數命名位置; 可以更快速地恢復整數）。 因此，相同字串的所有替代比對皆可導向相同的位置。 萬一發生衝突時，最後一個進入位置的比對就是成功的比對 (不過，您可以使用單一位置之多個比對的完整清單。 請參閱<xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>集合，如需詳細資訊。)  
  
## <a name="see-also"></a>另請參閱  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)
