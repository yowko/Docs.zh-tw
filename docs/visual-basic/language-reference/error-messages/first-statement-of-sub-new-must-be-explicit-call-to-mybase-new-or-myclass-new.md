---
title: "這個 'Sub New' 的第一個陳述式必須是對 'MyBase.New' 或 'MyClass.New' 的明確呼叫，因為 '<constructorname>' 的基底類別 '<baseclassname>' 中的 '<derivedclassname>' 標記為過時: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 33dd15e3f5f5538963597f2b00f4214895e1f47a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403001"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>這個 'Sub New' 的第一個陳述式必須是對 'MyBase.New' 或 'MyClass.New' 的明確呼叫，因為 '\<constructorname>' 的基底類別 '\<baseclassname>' 中的 '\<derivedclassname>' 標記為過時: '\<errormessage>'
類別建構函式未明確地呼叫基底類別建構函式，而且隱含的基底類別建構函式已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記，以將其視為錯誤。  
  
 當衍生類別的函式不會呼叫基類（class）時，Visual Basic 會嘗試產生無參數的基類（class）的隱含呼叫。 如果無法在沒有引數的情況下呼叫的基類中沒有可存取的函式，Visual Basic 就無法產生隱含的呼叫。 在此情況下，所需的函式會以 <xref:System.ObsoleteAttribute> 屬性標記，因此 Visual Basic 無法呼叫它。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute> 。 如果您這麼做，則可以將屬性 (attribute) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 (property) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤識別碼：** BC30920  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢查引用的錯誤訊息，並採取適當的動作。  
  
2. 包含 `MyBase.New()` 或 `MyClass.New()` 的呼叫作為衍生類別中 `Sub New` 的第一個陳述式。  
  
## <a name="see-also"></a>另請參閱

- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
