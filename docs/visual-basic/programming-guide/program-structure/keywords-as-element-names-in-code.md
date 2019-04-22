---
title: 程式碼中以關鍵字做為項目名稱 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841143"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>程式碼中以關鍵字做為項目名稱 (Visual Basic)
任何程式項目，例如變數、 類別或成員，可以有相同名稱做為受限制的關鍵字。 例如，您可以建立名為的變數`Loop`。 不過，來參考它的版本，具有相同名稱的限制`Loop`關鍵字，您必須前面使用完整限定性條件字串，或將它括在方括號 (`[ ]`)，如下列範例所示。  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 如果你未執行任一種，則 Visual Basic 會假設使用內建函式`Loop`關鍵字，並產生錯誤，如下列範例所示：  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 您可以使用方括號，當參考表單和控制項，以及當宣告的變數，或做為限制關鍵字定義具有相同名稱的程序。 它可以很容易忘記來限定名稱，或包含方括號，因此引入您的程式碼中的錯誤並讓它更難讀取。 基於這個理由，我們建議您不要使用限制的關鍵字做為程式項目的名稱。 不過，如果未來的 Visual Basic 版本定義新的關鍵字，與現有的表單或控制項名稱的衝突，然後您可以使用這項技術更新您的程式碼時才能使用新的版本。  
  
> [!NOTE]
>  您的程式也可能包含其他參考的組件所提供的項目名稱。 如果與限制關鍵字，這些名稱衝突，然後將其周圍的方括號會使 Visual Basic，以將它們解譯為您定義的項目。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
