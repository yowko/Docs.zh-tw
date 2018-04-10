---
title: Default (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
將屬性識別為其類別、 結構或介面的預設屬性。  
  
## <a name="remarks"></a>備註  
 類別、 結構或介面可以指定最多一個做為其屬性*預設屬性*，前提是屬性會使用至少一個參數。 如果程式碼會產生類別或結構的參考，而不指定的成員，Visual Basic 會解析該參考的預設屬性。  
  
 預設屬性可能會導致小型減少原始程式碼字元，但它們可讓您的程式碼更難閱讀。 如果類別或結構名稱的參考時呼叫的程式碼不熟悉您自己的類別或結構，它無法確定該參考存取類別或結構本身或預設屬性。 這可能會導致編譯器錯誤或難以察覺的執行階段邏輯錯誤。  
  
 您可以稍微降低預設屬性錯誤的機率都使用[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)設定要檢查的編譯器型別`On`。  
  
 如果您打算使用預先定義的類別或結構中程式碼，您必須判斷是否具有預設屬性，而且如果是，它的名稱為何。  
  
 由於這些缺點，您應該考慮不要定義預設屬性。 程式碼的可讀性，您應該也會考慮一律明確地參考所有屬性，甚至是預設屬性。  
  
 `Default`修飾詞可用於此內容：  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
