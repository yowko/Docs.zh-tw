---
title: "宣告項目特性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26ee27d3a1d085c6ab45ae850dbdac700aa208a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="declared-element-characteristics-visual-basic"></a>宣告項目特性 (Visual Basic)
A*特性*宣告的項目是會影響程式碼可以使用了該項目的外觀。 每個宣告的項目有一或多個與它相關的下列特性：  
  
-   *資料型別*— 項目可以保留的值，以及如何儲存這些值。 如需詳細資訊，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
-   *存留期*— 這段期間的項目是可供使用的執行時間。 如需詳細資訊，請參閱[在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   *範圍*— 可以參考項目而不需要限定其名稱的所有程式碼。 如需詳細資訊，請參閱[如何： 控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)。  
  
-   *存取層級*： 進行程式碼的權限的項目使用。 如需詳細資訊，請參閱[如何： 控制變數的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)。  
  
## <a name="characteristics-of-the-elements"></a>項目特性  
 下表顯示宣告的項目，並套用至每一個的特性。  
  
|項目|資料類型|存留期|範圍<sup>1</sup>|存取層級|  
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
|事件|否|否|是|是|  
|委派|否|否|是|是|  
  
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
