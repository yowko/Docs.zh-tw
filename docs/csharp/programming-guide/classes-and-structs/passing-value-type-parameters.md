---
title: "傳遞實值型別的參數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a780a11d8dd238187eb82933359bbb151bb3c333
ms.openlocfilehash: b0735f9a42fad01695c1ad64cfb937dce8e3cb93
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="passing-value-type-parameters-c-programming-guide"></a>傳遞實值類型的參數 (C# 程式設計手冊)
相對於[參考型別](../../../csharp/language-reference/keywords/reference-types.md)變數 (包含對其資料的參考)，[實值型別](../../../csharp/language-reference/keywords/value-types.md)變數會直接包含資料。 以傳值方式將實值型別變數傳遞至方法，意味著將變數的複本傳遞至方法。 任何發生於方法內部的參數變更都不會影響儲存於引數變數中的原始資料。 如果您想要讓呼叫的方法變更參數值，就必須使用 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 關鍵字，以傳址方式來傳遞它。 為求簡化，下列範例使用 `ref`。  
  
## <a name="passing-value-types-by-value"></a>以傳值方式傳遞實值型別  
 下列範例示範以傳值方式傳遞實值型別參數。 `n` 變數會以傳值方式傳遞至 `SquareIt` 方法。 任何發生在方法內部的變更都不會影響變數的原始值。  
  
 [!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 `n` 變數是實值型別。 它包含值為 `5` 的資料。 叫用 `SquareIt` 時，會將 `n` 的內容複製到 `x` 參數，並在方法內部將其平方。 不過，在 `Main` 中，`n` 的值在呼叫`SquareIt` 方法前後是一樣的。 發生在方法內部的變更只會影響區域變數 `x`。  
  
## <a name="passing-value-types-by-reference"></a>以傳址方式傳遞實值型別  
 下列範例與上述範例相同，差別在於引數是以 `ref` 參數來傳遞。 當方法中的 `x` 變更時，基礎引數的值 (`n`) 也會變更。  
  
 [!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 在此範例中，它不是所傳遞之 `n` 的值；而是傳遞對 `n` 的參考。 `x` 參數不是 [int](../../../csharp/language-reference/keywords/int.md)；它是對 `int` 的參考，在此案例中，為對 `n` 的參考。 因此，在方法內部將 `x` 平方時，實際平方的是 `x` 所參考的目標，即 `n`。  
  
## <a name="swapping-value-types"></a>交換實值型別  
 變更引數值的常見範例是 swap 方法，您會在其中將兩個變數傳遞至方法，而此方法會交換它們的內容。 您必須以傳址方式將引數傳遞至 swap 方法。 否則，您會交換方法內部參數的區域複本，而不會在呼叫方法中發生任何變更。 下例會交換整數值。  
  
 [!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 當您呼叫 `SwapByRef` 方法時，請在呼叫中使用 `ref` 關鍵字，如下列範例所示。  
  
 [!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [傳遞參數](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [傳遞參考型別參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
