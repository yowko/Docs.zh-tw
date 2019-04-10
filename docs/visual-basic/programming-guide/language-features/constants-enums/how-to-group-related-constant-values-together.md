---
title: HOW TO：群組相關聯的常值放在一起 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: a4f74e48cfdd5c0bc0f745d0f32eb39442f5bd83
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333323"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>HOW TO：群組相關聯的常值放在一起 (Visual Basic)
列舉是相關的常數群組在一起的最佳方式。 您建立的列舉`Enum`「 宣告 」 區段中的類別或模組的陳述式。 如需詳細資訊，請參閱[如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)。  
  
### <a name="to-group-related-constant-values"></a>群組關聯的常數值  
  
1. 撰寫包含程式碼存取層級中，宣告`Enum`關鍵字，且有效的名稱。 這個範例會建立`Private`列舉型別， `temperatureValues`。  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. 列舉中定義的常數。 這個範例會建立`Public`列舉型別`temperatureValues`並指派其值。  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [HOW TO：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [何時使用列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [常數概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
