---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
指定 Visual Basic 應封送處理字串根據.NET Framework 外部的程序所宣告的外部名稱為基礎的規則。  
  
 當您呼叫在專案外部定義的程序時，Visual Basic 編譯器並沒有存取它必須能夠正確地呼叫程序的資訊。 此資訊包括程序所在的位置、 如何識別、 它的呼叫順序和傳回型別，以及字串字元設定它使用。 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供此必要資訊。  
  
 `charsetmodifier`的一部分`Declare`陳述式提供給外部程序呼叫期間封送處理字串的字元組資訊。 它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。 `Auto`修飾詞會指定 Visual Basic 應該根據.NET Framework 規則字串封送處理和，應該判斷基底字元集的執行階段平台，且可能修改外部程序名稱，如果初始搜尋將會失敗。 如需詳細資訊，請參閱 「 字元集 」 中[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)。  
  
 如果未不指定任何字元 set 修飾詞，則`Ansi`是預設值。  
  
## <a name="remarks"></a>備註  
 `Auto`修飾詞可用於此內容：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援此關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
