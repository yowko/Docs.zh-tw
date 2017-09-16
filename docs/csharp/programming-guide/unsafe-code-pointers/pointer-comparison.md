---
title: "指標比較 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: 14
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
ms.openlocfilehash: a68a9a419349b8ba09afa27f09086f8316fd0583
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-comparison-c-programming-guide"></a>指標比較 (C# 程式設計手冊)
您可以套用下列運算子來比較任何類型的指標：  
  
 **==   !=   \<   >   \<=   >=**  
  
 比較運算子會比較兩個運算元的位址，就像它們是不帶正負號的整數一樣。  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-cs[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a>範例輸出  
 `True`  
  
 `False`  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)   
 [指標操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

