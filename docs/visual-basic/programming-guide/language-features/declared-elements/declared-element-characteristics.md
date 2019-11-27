---
title: 宣告項目特性
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
ms.openlocfilehash: 4e03cd28fed5e0ae109337739251c11a0ff3424a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331631"
---
# <a name="declared-element-characteristics-visual-basic"></a>宣告項目特性 (Visual Basic)
已宣告專案的*特性*是該專案的一個層面，會影響程式碼與它互動的方式。 每個宣告的元素都有一或多個相關聯的下列特性：  
  
- *資料類型*—元素可以保存的值，以及儲存這些值的方式。 如需詳細資訊，請參閱[資料類型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
- *存留*期-專案可供使用的執行時間期間。 如需詳細資訊，請參閱[Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
- *範圍*-可以參考專案但不限定其名稱的所有程式碼集合。 如需詳細資訊，請參閱[如何：控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)。  
  
- *存取層級*-程式碼用來利用專案的許可權。 如需詳細資訊，請參閱[如何：控制變數的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)。  
  
## <a name="characteristics-of-the-elements"></a>元素的特性  
 下表顯示已宣告的專案，以及套用至每一個專案的特性。  
  
|項目|資料型別|存留期|範圍<sup>1</sup>|存取層級|  
|-------------|---------------|--------------|------------------------|------------------|  
|變數|是|是|是|是|  
|常數|是|否|是|是|  
|列舉|是|否|是|是|  
|結構|否|否|是|是|  
|屬性|是|是|是|是|  
|方法|否|是|是|是|  
|程式（`Sub` 或 `Function`）|否|是|是|是|  
|程序參數|是|是|是|否|  
|函數傳回|是|是|是|否|  
|運算子|是|否|是|是|  
|介面|否|否|是|是|  
|執行個體|否|否|是|是|  
|事件|否|否|是|是|  
|委派|否|否|是|是|  
  
 <sup>1</sup>範圍有時稱為*可見度*。  
  
## <a name="see-also"></a>另請參閱

- [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
