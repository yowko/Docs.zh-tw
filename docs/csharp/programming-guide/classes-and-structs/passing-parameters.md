---
title: "傳遞參數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a4004cb22dfd23d24c6c333a560cb89b8ab08771
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="passing-parameters-c-programming-guide"></a>傳遞參數 (C# 程式設計手冊)
在 C# 中，引數可以由傳值或傳址方式傳遞至參數。 以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。 若要以傳址方式傳遞參數，請使用 `ref` 或 `out` 關鍵字。 為簡化起見，本主題的範例中只使用 `ref` 關鍵字。 如需 `ref` 與 `out` 差異的詳細資訊，請參閱 [ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out.md) 和[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。  
  
 下例會說明值和參考參數之間的差異。  
  
 [!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [傳遞實值型別參數](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [傳遞參考型別參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)
