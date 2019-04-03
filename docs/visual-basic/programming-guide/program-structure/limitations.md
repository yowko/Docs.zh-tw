---
title: Visual Basic 的限制
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 10f67c02d25ec275d1c3e98197d51c25aa250c19
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824906"
---
# <a name="visual-basic-limitations"></a>Visual Basic 的限制
舊版的 Visual Basic 會強制執行中程式碼，例如變數名稱，變數中的模組，以及模組大小所允許的數目的長度的界限。 在 Visual Basic.NET 中，這些限制已經被放寬，讓您更充分的自由撰寫及排列您的程式碼。  
  
 實體的限制會更依賴於執行階段的記憶體，比在編譯時期的考量。 如果您使用容錯度加倍的程式設計作法，並分成多個類別和模組中的大型應用程式時，就很少機會遇到內部的 Visual Basic 限制。  
  
 以下是在極端情況下可能會遇到一些限制：  
  
-   **名稱長度。** 沒有最大的每個宣告的程式設計項目名稱的字元數。 如果為限定的項目名稱，這個最大值會套用到整個限定性條件字串。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   **行長度。** 沒有實體的來源程式碼行中的 65535 個字元的最大值。 如果您使用行接續字元的長度時，能邏輯的原始程式碼行。 請參閱[如何：中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
-   **陣列維度。** 沒有您可以宣告為陣列的維度數目上限。 這會限制您可以使用指定的陣列元素的幾個索引。 請參閱[Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
-   **字串長度。** 沒有您可以儲存在單一字串的 Unicode 字元的數目上限。 請參閱[字串資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
-   **環境字串長度。** 沒有任何做為命令列引數的環境字串 32768 個字元的最大值。 這是在所有平台上的限制。  
  
## <a name="see-also"></a>另請參閱

- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
