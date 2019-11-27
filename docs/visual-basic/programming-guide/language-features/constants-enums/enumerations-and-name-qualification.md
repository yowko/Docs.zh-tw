---
title: 列舉和名稱限定性條件
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347502"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>列舉和名稱限定 (Visual Basic)
一般來說，在參考列舉的成員時，您必須使用列舉名稱來限定成員名稱。 例如，若要參考 `Days` 列舉的 `Sunday` 成員，您可以使用下列語法：  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>使用 Imports 語句  
 您可以藉由將 `Imports` 語句加入程式碼的命名空間宣告區段，來避免使用完整名稱，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports` 語句會從參考的專案和元件中匯入命名空間名稱，並從與語句出現所在模組的相同專案中匯入。 新增此語句之後，您可以參考列舉成員，而不需要限定，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 藉由組織列舉中的相關常數集，您可以在不同的內容中使用相同的常數名稱。 例如，您可以將相同的名稱用於 `Days` 中的工作日常數，並 `WorkDays` 列舉。 如果您搭配列舉使用 `Imports` 語句，必須小心避免不明確的參考。 參考下列範例：  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 假設 `Monday` 同時是 `Days` 列舉和 `Workdays` 列舉的成員，則此程式碼會產生編譯器錯誤。 若要在參考個別常數時避免不明確的參考，請使用其列舉來限定常數名稱。 下列程式碼會參考 `Days` 和 `WorkDays` 列舉中的 `Saturday` 常數。  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>請參閱

- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [如何：在 Visual Basic 中逐一查看列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
