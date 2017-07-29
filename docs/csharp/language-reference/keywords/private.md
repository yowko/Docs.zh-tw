---
title: "private (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
dev_langs:
- CSharp
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
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
ms.openlocfilehash: c18fd87b12bf3f7f1a1d1ef0dfded8643308169c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="private-c-reference"></a>private (C# 參考)
`private` 關鍵字是成員存取修飾詞。 私用存取是最嚴格的存取層級。 私用成員只能在宣告它們的類別主體或結構主體內存取，如本範例所示：  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 相同主體內的巢狀型別也可以存取這些私用成員。  
  
 在宣告私用成員的類別或結構外部參考私用成員是編譯時期錯誤。  
  
 如需 `private` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
## <a name="example"></a>範例  
 在此範例中，`Employee` 類別包含兩個私用資料成員：`name` 和 `salary`。 作為私用成員，只有成員方法能加以存取。 因此會新增名為 `GetName` 和 `Salary` 的公用方法，以允許對這些私用成員的控制存取。 `name` 成員是透過公用方法存取，`salary` 成員則是透過公用唯讀屬性存取 (如需詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md))。  
  
 [!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)

