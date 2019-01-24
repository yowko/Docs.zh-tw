---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;methodname&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: ff9ffd50f7f21814d5e4c23fd8df50b12bf746f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642435"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;methodname&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;
類別或結構宣告實作介面，但不會實作該介面所定義的程序。 必須實作介面的每個成員。  
  
 **錯誤 ID:** BC30149  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  宣告具有相同的名稱與簽章的介面中所定義的程序。 務必要包含在至少`End Function`或`End Sub`陳述式。  
  
2.  新增`Implements`子句來結束`Function`或`Sub`陳述式。 例如:   
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>另請參閱
- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
