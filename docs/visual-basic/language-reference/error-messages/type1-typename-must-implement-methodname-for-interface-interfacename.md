---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;methodname&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;type1&gt;&#39;&lt;typename&gt; &#39;必須實作&#39; &lt;methodname&gt; &#39;介面&#39;&lt;介面名稱&gt;&#39;
類別或結構實作介面宣告，但未實作介面所定義的程序。 必須實作介面的每個成員。  
  
 **錯誤 ID:** BC30149  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  宣告具有相同名稱和簽章的介面中所定義的程序。 務必包含最少為`End Function`或`End Sub`陳述式。  
  
2.  新增`Implements`子句結尾`Function`或`Sub`陳述式。 例如:   
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
