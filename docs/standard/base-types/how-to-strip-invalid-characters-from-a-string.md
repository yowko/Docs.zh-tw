---
title: "如何：從字串中刪除無效的字元"
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
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f676ca9121498da7c88cdec8b49586bde91b181
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>如何：從字串中刪除無效的字元
下列範例會使用靜態<xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>方法來刪除無效的字元字串。  
  
## <a name="example"></a>範例  
 您可以使用此範例中定義的 `CleanInput` 方法，去除使用者在文字欄位中可能已輸入的有害字元。 在此情況下，`CleanInput` 會去除句點 (.)、符號 (@) 以及連字號 (-) 以外的所有非英數字元，並傳回剩餘的字串。 不過，您可以修改規則運算式模式，讓它去除輸入字串中不應包含的任何字元。  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 規則運算式模式 `[^\w\.@-]` 會比對任何非文字字元的字元、句號、@ 符號或連字號。 文字字元是指任何字母、十進位數字或底線這類標點符號連接子。 符合此模式的任何字元會取代<xref:System.String.Empty?displayProperty=nameWithType>，這是取代模式所定義的字串。 若要允許使用者輸入其他字元，可將這些字元新增至規則運算式模式中的字元類別。 例如，規則運算式模式`[^\w\.@-\\%]`也允許在輸入字串的百分比符號和反斜線。  
  
## <a name="see-also"></a>另請參閱  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)
