---
title: Default (Visual Basic)
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
ms.openlocfilehash: b63fa66c9cda1e439e3917ca62377f68028fc049
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497837"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
將屬性識別為其類別、 結構或介面的預設屬性。  
  
## <a name="remarks"></a>備註  
 類別、 結構或介面可以指定最多為其屬性之一*屬性預設*，前提是屬性會採用至少一個參數。 如果程式碼會產生類別或結構的參考，但沒有指定成員，Visual Basic 會解析該參考的預設屬性。  
  
 預設屬性可能會導致小型減少原始程式碼字元，但它們可以讓您的程式碼更難讀取。 如果類別或結構名稱的參考時呼叫的程式碼不熟悉如何使用您自己的類別或結構，它無法確定該參考是存取類別或結構本身或預設屬性。 這可能會導致編譯器錯誤或難以察覺的執行階段邏輯錯誤。  
  
 您可以一律使用，以稍微降低預設屬性錯誤的機會[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)設定檢查的編譯器型別`On`。  
  
 如果您打算使用預先定義的類別或結構中您的程式碼中，您必須判斷是否有預設屬性，而如果是的話，它的名稱為何。  
  
 由於這些缺點，您應該考慮不要定義預設屬性。 程式碼的可讀性，您應該也要考慮一律明確地參考的所有屬性，甚至是預設屬性。  
  
 `Default`修飾詞，請使用此內容中：  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱
- [如何：宣告，並在 Visual Basic 中呼叫預設屬性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
