---
title: 限制
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347360"
---
# <a name="visual-basic-limitations"></a>Visual Basic 的限制
舊版 Visual Basic 在程式碼中強制執行界限，例如變數名稱的長度、模組中允許的變數數目，以及模組大小。 在 Visual Basic .NET 中，這些限制已經過寬鬆，讓您更能自由地撰寫和排列程式碼。  
  
 實體限制相依于執行時間記憶體，而不是編譯時期考慮。 如果您使用謹慎的程式設計實務，並將大型應用程式分割成多個類別和模組，那麼就沒有機會遇到內部 Visual Basic 限制。  
  
 以下是您在極端情況下可能會遇到的一些限制：  
  
- **名稱長度。** 每個宣告的程式設計項目的名稱都有最大的字元數。 如果專案名稱是限定的，此最大值會套用至整個限定性字串。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
- **行長度。** 在原始碼的實體行中，最多可有65535個字元。 如果您使用行接續字元，則邏輯源程式碼可能會較長。 請參閱[如何：在程式碼中中斷和合併語句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。  
  
- **陣列維度。** 您可以為陣列宣告的維度數目上限為。 這會限制您可以用來指定陣列元素的索引數目。 請參閱[Visual Basic 中的陣列維度](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
- **字串長度。** 您可以在單一字串中儲存的 Unicode 字元數目上限。 請參閱[String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
- **環境字串長度。** 做為命令列引數使用的任何環境字串，最多可有32768個字元。 這是所有平臺的限制。  
  
## <a name="see-also"></a>請參閱

- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
