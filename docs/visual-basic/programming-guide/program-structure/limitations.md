---
title: "Visual Basic 的限制 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d556b045b4ebae6ba24c0571a6cb7e5337c6a8f2
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-limitations"></a>Visual Basic 的限制
舊版的[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]強制執行中程式碼，例如變數名稱的長度界限中的模組，以及模組大小所允許的變數數目。 在[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]，這些限制已經放寬，讓您撰寫及排列您的程式碼更自由。  
  
 實體限制會更依賴於執行階段的記憶體比在編譯時期考量。 如果您使用審慎的程式設計作法，並將大型應用程式分割成多個類別和模組，則很極少機會遇到內部[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]限制。  
  
 以下是在極端情況下可能會遇到一些限制︰  
  
-   **名稱長度。** 沒有最大的每個宣告的程式設計項目名稱的字元數。 如果限定的項目名稱，這個最大值會套用到整個限定性條件字串。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   **行的長度。** 則實體一行程式碼中的 65535 個字元的上限。 邏輯來源一行程式碼會更長，如果您使用行接續字元。 請參閱[How to︰ 中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
-   **陣列維度。** 沒有您可以宣告陣列維度的數目上限。 這會限制多少可用來指定陣列元素的索引。 請參閱[陣列 Visual Basic 中的維度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
-   **字串長度。** 沒有您可以儲存在單一字串中的 Unicode 字元的數目上限。 請參閱[字串資料型別](../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
-   **環境字串長度。** 沒有 32768 個字元的任何環境字串做為命令列引數的最大值。 這是在所有平台上的限制。  
  
## <a name="see-also"></a>另請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
