---
title: "如何：取得指標變數值 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4cff42de07f2edb279ddd1cafefe9f4b67a38ce1
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>如何：取得指標變數值 (C# 程式設計手冊)
您可以使用指標間接運算子來取得指標所指向位置的變數。 運算式會採用下列格式，其中 `p` 是指標類型：  
  
```  
*p;  
```  
  
 您無法在非指標類型之任何類型的運算式上使用一元間接運算子。 此外，也無法將它套用至 [void](../../../csharp/language-reference/keywords/void.md) 指標。  
  
 當您將間接運算子套用至 [null](../../../csharp/language-reference/keywords/null.md) 指標時，結果會取決於實作。  
  
## <a name="example"></a>範例  
 在下列範例中，`char` 類型的變數會使用不同類型的指標來存取。 請注意，`theChar` 的位址會因執行而異，原因是配置給變數的實體位址可能會變更。  
  
 [!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 **值為 theChar = Z**   
**位址為 theChar = 12F718**  
**值為 pChar = Z**   
**值為 pInt = 90**    
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

