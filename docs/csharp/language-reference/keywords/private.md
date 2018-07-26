---
title: private (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 89bc23e91bf693f0a95b75dffe2399cb7e865b50
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960803"
---
# <a name="private-c-reference"></a>private (C# 參考)
`private` 關鍵字是成員存取修飾詞。 
   
 > 此頁面涵蓋 `private` 存取。 `private` 關鍵字也是屬於 [`private protected`](./private-protected.md) 存取修飾詞。
  
私用存取是最嚴格的存取層級。 私用成員只能在宣告它們的類別主體或結構主體內存取，如本範例所示：  
  
```csharp  
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
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
