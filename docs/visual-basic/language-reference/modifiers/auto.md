---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351623"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
指定 Visual Basic 應根據所宣告外部程式的外部名稱，依據 .NET Framework 規則封送處理字串。  
  
 當您呼叫在專案外部定義的程式時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊。 此資訊包括程式所在位置、識別方式、其呼叫順序和傳回類型，以及它所使用的字串字元集。 [Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程式的參考，並提供此必要資訊。  
  
 `Declare` 語句中的 `charsetmodifier` 部分會在呼叫外部程式期間提供封送處理字串的字元集資訊。 它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。 `Auto` 修飾詞會指定 Visual Basic 應該根據 .NET Framework 規則封送處理字串，而且它應該決定執行時間平臺的基底字元集，如果初始搜尋失敗，則可能會修改外部程式名稱。 如需詳細資訊，請參閱[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)中的「字元集」。  
  
 如果未指定任何字元集修飾詞，`Ansi` 為預設值。  
  
## <a name="remarks"></a>備註  
 `Auto` 修飾詞可以在此內容中使用：  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援這個關鍵字。  
  
## <a name="see-also"></a>請參閱

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
