---
title: Visual Basic 的限制
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d06b743996969dcd7fc022bbb8ab625f3a151137
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="visual-basic-limitations"></a>Visual Basic 的限制
舊版的 Visual Basic 會強制界限的程式碼，例如變數名稱的模組和模組大小中允許的變數數目的長度。 在 Visual Basic.NET 中，這些限制有已經放寬，讓您更自由撰寫及排列您的程式碼。  
  
 實體限制會更依賴於執行階段的記憶體比編譯時期的考量。 如果您使用審慎的程式設計作法，並將大型應用程式分割成多個類別和模組時，就很少機會遇到內部的 Visual Basic 限制。  
  
 在極端情況下可能會遇到一些限制如下：  
  
-   **名稱長度。** 沒有最大的每個宣告的程式設計項目名稱的字元數。 如果限定的項目名稱，這個最大值會套用到整個限定性條件字串。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   **行長度。** 沒有最多 65535 個字元的實體來源的程式碼行。 一行程式碼邏輯來源可以是較長，如果您使用行接續字元。 請參閱[How to： 中斷和合併陳述式中的程式碼](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
-   **陣列維度。** 沒有您可以宣告為陣列的維度數目上限。 這會限制多少索引可用來指定陣列項目。 請參閱[陣列 Visual Basic 中的維度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
-   **字串長度。** 沒有您可以儲存在單一字串中的 Unicode 字元的數目上限。 請參閱[字串資料型別](../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
-   **環境字串長度。** 沒有 32768 字元做為命令列引數的任何環境字串的最大值。 這是在所有平台上的限制。  
  
## <a name="see-also"></a>另請參閱  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
