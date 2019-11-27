---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344215"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
指定 Visual Basic 應該將所有字串封送處理成 Unicode 值，而不論所宣告的外部程式名稱為何。  
  
 當您呼叫在專案外部定義的程式時，Visual Basic 編譯器無法存取其所需的資訊，以便正確地呼叫程式。 此資訊包括程式所在位置、識別方式、其呼叫順序和傳回類型，以及它所使用的字串字元集。 [Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程式的參考，並提供此必要資訊。  
  
 `Declare` 語句中的 `charsetmodifier` 部分會提供字元集資訊，以便在呼叫外部程式期間封送處理字串。 它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。 `Unicode` 修飾詞指定 Visual Basic 應該將所有字串封送處理成 Unicode 值，而且在搜尋過程中，不需要修改其名稱，就應該查閱程式。  
  
 如果未指定任何字元集修飾詞，`Ansi` 為預設值。  
  
## <a name="remarks"></a>備註  
 `Unicode` 修飾詞可以在此內容中使用：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援這個關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
