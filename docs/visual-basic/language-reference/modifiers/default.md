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
ms.openlocfilehash: bc213c3b5564d1833136df8f5b8dab1c6b012296
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875493"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)

將屬性識別為其類別、結構或介面的預設屬性。  
  
## <a name="remarks"></a>備註  

 類別、結構或介面最多可將其中一個屬性指定為 *預設屬性*，前提是該屬性至少接受一個參數。 如果程式碼在沒有指定成員的情況下參考類別或結構，Visual Basic 會將該參考解析為預設屬性。  
  
 預設屬性可能會減少原始程式碼字元，但可以讓您的程式碼更難以讀取。 如果呼叫程式碼不熟悉您的類別或結構，則在參考類別或結構名稱時，如果該參考存取類別或結構本身或預設屬性，則無法確定。 這可能會導致編譯器錯誤或微妙的執行時間邏輯錯誤。  
  
 您可以使用 [Option Strict 語句](../statements/option-strict-statement.md) 將編譯器類型檢查設定為，以稍微減少預設屬性錯誤的機率 `On` 。  
  
 如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱就是。  
  
 因為這些缺點，您應該考慮不要定義預設屬性。 為了讓程式碼更容易閱讀，您也應該考慮一律明確參考所有屬性，甚至是預設屬性。  
  
 `Default`修飾詞可用於此內容中：  
  
 [Property Statement](../statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [如何：在 Visual Basic 中宣告及呼叫預設屬性](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [關鍵字](../keywords/index.md)
