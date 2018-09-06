---
title: 宣告項目特性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 27dad8b2fbfbc8d17090df201bf36eb080966f51
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037970"
---
# <a name="declared-element-characteristics-visual-basic"></a>宣告項目特性 (Visual Basic)
A*特性*的宣告的項目是如何與其互動的程式碼會影響該元素的層面。 每個宣告的項目有一或多個與它相關的下列特性：  
  
-   *資料型別*-項目可以保留的值，以及它如何儲存這些值。 如需詳細資訊，請參閱[資料類型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
-   *存留期*— 這段期間執行期間的項目是可供使用。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   *範圍*— 可以參考的項目未限定其名稱的所有程式碼的集合。 如需詳細資訊，請參閱 <<c0> [ 如何： 控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)。  
  
-   *存取層級*— 進行程式碼的權限使用的項目。 如需詳細資訊，請參閱 <<c0> [ 如何： 控制變數的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)。  
  
## <a name="characteristics-of-the-elements"></a>項目特性  
 下表顯示宣告的項目並套用至每一個的特性。  
  
|元素|資料類型|存留期|範圍<sup>1</sup>|存取層級|  
|-------------|---------------|--------------|------------------------|------------------|  
|變數|是|是|是|是|  
|常數|是|否|是|是|  
|列舉|是|否|是|是|  
|結構|否|否|是|是|  
|屬性|是|是|是|是|  
|方法|否|是|是|是|  
|程序 (`Sub`或`Function`)|否|是|是|是|  
|程序參數|是|是|是|否|  
|函式傳回|是|是|是|否|  
|運算子|是|否|是|是|  
|介面|否|否|是|是|  
|類別|否|否|是|是|  
|Event - 事件|否|否|是|是|  
|Delegate - 委派|否|否|是|是|  
  
 <sup>1</sup>範圍有時稱為*可視性*。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
