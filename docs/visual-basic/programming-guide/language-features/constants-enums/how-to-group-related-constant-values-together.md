---
title: 如何：將關聯的常數值群組在一起 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 320373116ad4d61293690353fce6b7b152e79a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646399"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>如何：將關聯的常數值群組在一起 (Visual Basic)
列舉類型是最佳的方式來分組相關的常數。 建立列舉，含`Enum`陳述式的宣告區段中的類別或模組。 如需詳細資訊，請參閱[如何： 宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)。  
  
### <a name="to-group-related-constant-values"></a>群組關聯的常數值  
  
1.  撰寫包含程式碼存取層級中，宣告`Enum`關鍵字，且是有效的名稱。 這個範例會建立`Private`列舉型別， `temperatureValues`。  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  列舉型別中定義的常數。 這個範例會建立`Public`列舉`temperatureValues`並指派其值。  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
