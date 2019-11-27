---
title: 預設
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351573"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
將屬性識別為其類別、結構或介面的預設屬性。  
  
## <a name="remarks"></a>備註  
 類別、結構或介面最多可以指定其中一個屬性做為*預設屬性*，前提是該屬性至少接受一個參數。 如果程式碼在不指定成員的情況下參考類別或結構，Visual Basic 會將該參考解析為預設屬性。  
  
 預設屬性可能會減少原始碼字元數，但它們可能會使您的程式碼更容易閱讀。 如果呼叫程式碼不熟悉您的類別或結構，當它對類別或結構名稱進行參考時，就無法確定該參考是要存取類別或結構本身，還是預設屬性。 這可能會導致編譯器錯誤或細微的執行時間邏輯錯誤。  
  
 您可以一律使用[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)，將編譯器類型檢查設定為 `On`，藉此減少預設屬性錯誤的機率。  
  
 如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱為何。  
  
 由於這些缺點，您應該考慮不要定義預設屬性。 為了讓程式碼更容易閱讀，您也應該考慮明確參考所有屬性，甚至是預設屬性。  
  
 `Default` 修飾詞可以在此內容中使用：  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [如何：在 Visual Basic 中宣告及呼叫預設屬性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
