---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843834"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
指定 Visual Basic 應封送處理根據.NET Framework 的規則，根據所宣告外部程序的外部名稱的字串。  
  
 當您呼叫在專案以外定義的程序時，Visual Basic 編譯器並沒有存取它必須正確地呼叫程序的資訊。 此資訊包括程序所在的位置、 其識別方式、 其呼叫的順序和傳回型別，以及字串字元設定它使用。 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這些必要的資訊。  
  
 `charsetmodifier`部分`Declare`陳述式提供在外部的程序呼叫封送處理字串的字元組資訊。 它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。 `Auto`修飾詞會指定 Visual Basic 應該根據.NET Framework 規則的字串封送處理和它應該決定設定的執行階段平台和可能的基底字元，修改外部程序名稱如果初始搜尋將會失敗。 如需詳細資訊，請參閱 < 字元集 」 中[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)。  
  
 如果未不指定任何字元組修飾詞，則`Ansi`是預設值。  
  
## <a name="remarks"></a>備註  
 `Auto`修飾詞，請使用此內容中：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援此關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
