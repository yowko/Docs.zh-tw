---
title: "如何：宣告及使用讀寫屬性 (C# 程式設計指南)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e5e4ca1feff203dc2ab88c0d1dfae8098508fec7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>如何：宣告及使用讀寫屬性 (C# 程式設計指南)
屬性會提供公用資料成員的便利性，卻沒有不受保護、控制和驗證存取物件資料所附帶的風險。 這是透過「存取子」完成的：從基礎資料成員指派和擷取值的特殊方法。 [set](../../../csharp/language-reference/keywords/set.md) 存取子可讓資料成員被指派，而 [get](../../../csharp/language-reference/keywords/get.md) 存取子可擷取資料成員值。  
  
 這個範例會示範有兩個屬性的 `Person` 類別：`Name` (字串) 和 `Age` (整數)。 這兩個屬性都提供 `get` 和 `set` 存取子，所以它們被視為讀取/寫入屬性。  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 在上例中，`Name` 和 `Age` 屬性是[公用的](../../../csharp/language-reference/keywords/public.md)，且同時包含 `get` 和 `set` 存取子。 這可讓任何物件讀取和寫入這些屬性。 但有時候會很想排除其中一個存取子。 例如，省略 `set` 存取子會讓屬性變成唯讀的：  
  
 [!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 或者，您也可以向公眾公開某個存取子，但讓其他存取子為私用或受保護的。 如需詳細資訊，請參閱[非對稱存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
 屬性一旦宣告，即可當成類別的欄位使用。 這在取得和設定屬性值時，可使用非常自然的語法，如下列陳述式所示：  
  
 [!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 請注意，在屬性 `set` 方法中提供特殊的 `value` 變數。 此變數包含使用者指定的值，例如：  
  
 [!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 請注意在 `Person` 物件上遞增 `Age` 屬性的全新語法：  
  
 [!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 如果分別使用 `set` 和 `get` 方法建立了屬性模型，對等的程式碼可能看起來像這樣：  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 本例中覆寫 `ToString` 方法：  
  
 [!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 請注意，程式中未明確使用 `ToString`。 預設會由 `WriteLine` 呼叫叫用。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)

