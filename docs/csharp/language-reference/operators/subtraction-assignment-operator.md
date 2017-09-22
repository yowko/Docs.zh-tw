---
title: "-= 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
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
ms.openlocfilehash: d7f26ae1fce54eb0d03a314a83ce523baeb3f348
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="--operator-c-reference"></a>-= 運算子 (C# 參考)
減法指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `-=` 指派運算子的運算式，例如  
  
```  
x -= y  
```  
  
 相當於  
  
```  
x = x - y  
```  
  
 但只會評估 `x` 一次。 [- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) 的意義取決於 `x` 和 `y` 的類型 (數字運算元表示減法、委派運算元表示委派移除等等)。  
  
 無法直接多載 `-=` 運算子，但使用者定義型別可以多載 [- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
 -= 運算子也會用於 C# 中，以取消事件的訂閱。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。  
  
## <a name="example"></a>範例  
 [!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)

