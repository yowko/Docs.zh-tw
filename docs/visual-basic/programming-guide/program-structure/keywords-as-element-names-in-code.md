---
title: 程式碼中的項目名稱關鍵字
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: a98f0b027700717b414d58e1284ddec655eb25f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403222"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>程式碼中以關鍵字做為項目名稱 (Visual Basic)
任何程式元素（例如變數、類別或成員）的名稱都可以與受限關鍵字相同。 例如，您可以建立名為的變數 `Loop` 。 不過，若要參考您的版本（其名稱與受限制的 `Loop` 關鍵字相同），您必須在其前面加上完整限定字串，或將其括在方括弧（ `[ ]` ）中，如下列範例所示。  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 如果您未執行上述任一項，則 Visual Basic 會假設使用內建 `Loop` 關鍵字並產生錯誤，如下列範例所示：  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 您可以在參考表單和控制項時，以及在宣告變數或使用與受限制關鍵字相同的名稱來定義程式時，使用方括弧。 您可能很容易忘記限定名稱或包含方括弧，因此在您的程式碼中引進錯誤，使其更難以閱讀。 基於這個理由，我們建議您不要使用受限制的關鍵字做為程式元素的名稱。 不過，如果 Visual Basic 的未來版本定義了與現有表單或控制項名稱衝突的新關鍵字，則在更新程式碼以使用新版本時，您可以使用這項技術。  
  
> [!NOTE]
> 您的程式也可能包含其他參考元件所提供的元素名稱。 如果這些名稱與受限制的關鍵字衝突，則在其周圍加上方括弧會導致 Visual Basic 將它們解讀為您定義的元素。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命名慣例](naming-conventions.md)
- [程式結構和程式碼慣例](program-structure-and-code-conventions.md)
- [關鍵字](../../language-reference/keywords/index.md)
