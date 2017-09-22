---
title: "如何：使用 as 和 is 運算子進行安全轉型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
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
ms.openlocfilehash: c5daa8525f45c123dabb0f59dfd29385b9e50354
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>如何：使用 as 和 is 運算子進行安全轉型 (C# 程式設計手冊)
因為物件都是多型的，所以可能會針對基底類別類型的變數來保存衍生類型。 若要存取衍生類型的方法，就需要將值轉換回衍生類型。 不過，在這些情況下嘗試簡單轉換，會造成擲回 <xref:System.InvalidCastException> 的風險。 這也就是為什麼 C# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 運算子的原因。 您可以使用這些運算子，來測試轉換是否成功而不會造成擲回例外狀況。 一般來說，`as` 運算子更有效率，因為如果轉換順利完成，它實際上會傳回轉換值。 `is` 運算子只會傳回布林值。 因此，當您只想要判斷物件的類型而不需要實際轉換時，才會使用此運算子。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `is` 和 `as` 運算子將某個參考型別轉換成另一個參考型別，而不會造成擲回例外狀況的風險。 此範例也示範如何使用 `as` 運算子與可為 Null 的實值型別。  
  
 [!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [類型](../../../csharp/programming-guide/types/index.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)

