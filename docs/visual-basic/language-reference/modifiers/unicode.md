---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 491bbb24be8e6a3044b0a433c5ad262596ae00d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655279"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
指定 Visual Basic 應封送處理為 Unicode 值，不論所宣告外部程序名稱的所有字串。  
  
 當您呼叫在專案以外定義的程序時，Visual Basic 編譯器並沒有存取它必須擁有才能正確地呼叫程序的資訊。 此資訊包括程序所在的位置、 其識別方式、 其呼叫的順序和傳回型別，以及字串字元設定它使用。 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這些必要的資訊。  
  
 `charsetmodifier`部分`Declare`陳述式提供在外部的程序呼叫封送處理字串的字元組資訊。 它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。 `Unicode`修飾詞會指定 Visual Basic 應封送處理為 Unicode 值的所有字串，並應該查閱而不需要在搜尋期間修改其名稱的程序。  
  
 如果未不指定任何字元組修飾詞，則`Ansi`是預設值。  
  
## <a name="remarks"></a>備註  
 `Unicode`修飾詞，請使用此內容中：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援此關鍵字。  
  
## <a name="see-also"></a>另請參閱
- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
