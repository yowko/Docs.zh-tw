---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;membername&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574738"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;membername&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;
'\<類型名稱 >' 必須實作'\<成員名稱 >' 的介面 '\<介面名稱 >'。 實作屬性必須比對 'ReadOnly '/' WriteOnly' 規範。  
  
 類別或結構宣告實作介面，但不會實作程序、 屬性或介面所定義的事件。 必須實作介面的每個成員。  
  
 **錯誤 ID:** BC30154  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  宣告具有相同的名稱和簽章的介面中所定義的成員。 務必要包含在至少`End Function`， `End Sub`，或`End Property`陳述式。  
  
2.  新增`Implements`子句來結束`Function`， `Sub`， `Property`，或`Event`陳述式。 例如:   
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  當實作的屬性，請確定`ReadOnly`或`WriteOnly`用於介面定義的相同方式。  
  
4.  當實作的屬性，宣告`Get`和`Set`程序，適當地。  
  
## <a name="see-also"></a>另請參閱
- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
