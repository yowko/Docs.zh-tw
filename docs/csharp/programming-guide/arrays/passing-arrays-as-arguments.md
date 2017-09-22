---
title: "傳遞陣列當做引數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
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
ms.openlocfilehash: 5e83c0c119bc1448be76f83416098158c7f5d684
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>傳遞陣列當做引數 (C# 程式設計手冊)
陣列可以作為引數傳遞至方法參數。 因為陣列是參考型別，所以方法可以變更項目的值。  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>傳遞一維陣列作為引數  
 您可以將初始化的一維陣列傳遞至方法。 例如，下列陳述式會將陣列傳送至列印方法。  
  
 [!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 下列程式碼顯示列印方法的部分實作。  
  
 [!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。  
  
 [!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在下列範例中，字串的陣列會初始化，並作為引數傳遞至字串的 `PrintArray` 方法。 此方法會顯示陣列的元素。 接著，會呼叫 `ChangeArray` 和`ChangeArrayElement` 方法，以顯示透過值傳送陣列引數不會阻止變更陣列元素。  
  
### <a name="code"></a>程式碼  
 [!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>傳遞多維陣列作為引數  
 將初始化的多維陣列傳遞至方法所使用的方式，與傳遞一維陣列的方式相同。  
  
 [!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 下列程式碼顯示可接受二維陣列作為其引數之列印方法的部分宣告。  
  
 [!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。  
  
 [!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在下列範例中，整數的二維陣列會初始化並傳遞至 `Print2DArray` 方法。 此方法會顯示陣列的元素。  
  
### <a name="code"></a>程式碼  
 [!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)

