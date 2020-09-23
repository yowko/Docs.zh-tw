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
ms.openlocfilehash: abe4acd5850aa6065bf4f6fd41bc610ede7ad13f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097952"
---
# <a name="visual-basic-limitations"></a>Visual Basic 的限制

舊版 Visual Basic 會在程式碼中強制執行界限，例如變數名稱的長度、模組中允許的變數數目，以及模組大小。 在 Visual Basic .NET 中，這些限制已經過寬鬆，讓您可以更輕鬆地撰寫和排列程式碼。  
  
 實體限制在執行時間記憶體上相依于編譯時期的考慮。 如果您使用審慎的程式設計做法，並將大型應用程式分成多個類別和模組，那麼幾乎有可能遇到內部 Visual Basic 限制。  
  
 以下是您在極端情況下可能會遇到的一些限制：  
  
- **名稱長度。** 每個宣告的程式設計專案的名稱都有最大字元數。 如果元素名稱是合格的，則這個最大值會套用至整個限定性字串。 請參閱 [Declared Element Names](../language-features/declared-elements/declared-element-names.md)。  
  
- **行長度。** 在實體的原始程式碼中，最多可以有65535個字元。 如果您使用行接續字元，則邏輯來源程式碼行可能會更長。 請參閱 [如何：在程式碼中中斷和合併語句](how-to-break-and-combine-statements-in-code.md)。  
  
- **陣列維度。** 您可以針對陣列宣告的維度數目上限。 這會限制您可以用來指定陣列元素的索引數目。 請參閱 [Visual Basic 中的陣列維度](../language-features/arrays/array-dimensions.md)。  
  
- **字串長度。** 您可以在單一字串中儲存的 Unicode 字元數上限。 請參閱 [字串資料類型](../../language-reference/data-types/string-data-type.md)。  
  
- **環境字串長度。** 作為命令列引數的任何環境字串，最多可有32768個字元。 這是所有平臺的限制。  
  
## <a name="see-also"></a>另請參閱

- [程式結構和程式碼慣例](program-structure-and-code-conventions.md)
- [Visual Basic 命名慣例](naming-conventions.md)
