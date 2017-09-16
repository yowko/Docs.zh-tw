---
title: "存取範圍層級 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
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
ms.openlocfilehash: 796802a407c486c1df5332d5b4920467f3a1171b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-levels-c-reference"></a>存取範圍層級 (C# 參考)
使用存取修飾詞 [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 [private](../../../csharp/language-reference/keywords/private.md) 來指定成員的下列其中一個已宣告存取範圍層級。  
  
|已宣告存取範圍|意義|  
|----------------------------|-------------|  
|`public`|未限制存取。|  
|`protected`|存取限於包含類別或衍生自包含類別的類型。|  
|`internal`|存取限於目前組件。|  
|`protected internal`|存取限於目前組件或衍生自包含類別的類型。|  
|`private`|存取限於包含類型。|  
  
 一個成員或類型只允許一個存取修飾詞，但合併使用 `protected internal` 時除外。  
  
 命名空間上不允許存取修飾詞。 命名空間沒有存取限制。  
  
 根據發生成員宣告的內容，僅允許某些已宣告存取範圍。 如果未在成員宣告中指定任何存取修飾詞，則會使用預設存取範圍。  
  
 未巢狀於其他類型中的最上層類型，只能有 `internal` 或 `public` 存取範圍。 這些類型的預設存取範圍是 `internal`。  
  
 巢狀型別 (即其他類型的成員) 可以有下表中所指出的已宣告存取範圍。  
  
|成員|預設成員存取範圍|允許的成員已宣告存取範圍|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|無|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal`|  
|`interface`|`public`|無|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 巢狀型別的存取範圍取決於其[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)，這是由成員的已宣告存取範圍和立即包含類型的存取範圍定義域所決定。 但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [使用存取範圍層級的限制](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)

