---
title: "委派類別&lt;classname&gt;&quot; 有沒有 Invoke 方法，所以此類型的運算式不可成為方法呼叫的目標 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ddc5ef0f0b3e9baa58f17dafb727e250c0fba9fd
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>委派類別&lt;classname&gt;' 有沒有 Invoke 方法，所以此類型的運算式不可成為方法呼叫的目標
呼叫`Invoke`透過委派失敗，因為`Invoke`委派類別未實作。  
  
 **錯誤識別碼︰** BC30220  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  確定委派類別的執行個體已建立並`Dim`陳述式和程序已被指派委派執行個體，但`AddressOf`運算子。  
  
2.  找出實作委派類別的程式碼，並確定它會實作`Invoke`程序。  
  
## <a name="see-also"></a>另請參閱  
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
