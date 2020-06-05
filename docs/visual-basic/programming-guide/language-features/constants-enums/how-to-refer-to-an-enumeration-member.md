---
title: 如何：參考列舉類型成員
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414410"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>如何：參考列舉成員 (Visual Basic)
列舉提供了一種便利的方式，可使用一組相關的常數，並將常數值與名稱產生關聯。 例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。  
  
 您可以避免使用完整名稱搭配 `Imports` 語句。 如需詳細資訊，請參閱列舉[和名稱限定](enumerations-and-name-qualification.md)性。  
  
### <a name="to-refer-to-an-enumeration-member"></a>參考列舉成員  
  
- 使用列舉限定成員名稱。 例如，下列範例會將列舉的 `Saturday` 成員指派 `FirstDayOfWeek` 給變數 `DayValue` 。  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [如何：宣告列舉類型](how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：在 Visual Basic 中逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉類型](when-to-use-an-enumeration.md)
