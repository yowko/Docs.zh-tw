---
title: '如何宣告和使用讀寫屬性-c # 程式設計指南'
description: '瞭解如何在 c # 中使用讀取/寫入屬性。 此範例包含兩個屬性，其中每個屬性都有 get 和 set 存取子，因此屬性是讀取/寫入。'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 75f3b4d6fa8595734cf1310c08281c26c829fd84
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899018"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>如何宣告和使用讀寫屬性 (c # 程式設計手冊) 

屬性會提供公用資料成員的便利性，卻沒有不受保護、控制和驗證存取物件資料所附帶的風險。 這是透過「存取子」完成的：從基礎資料成員指派和擷取值的特殊方法。 [set](../../language-reference/keywords/set.md) 存取子可讓資料成員被指派，而 [get](../../language-reference/keywords/get.md) 存取子可擷取資料成員值。  
  
 這個範例會示範有兩個屬性的 `Person` 類別：`Name` (字串) 和 `Age` (整數)。 這兩個屬性都提供 `get` 和 `set` 存取子，所以它們被視為讀取/寫入屬性。  
  
## <a name="example"></a>範例  

 [!code-csharp[properties#1](snippets/how-to-declare-and-use-read-write-properties/Program.cs#1)]
  
## <a name="robust-programming"></a>穩固程式設計  

 在上例中，`Name` 和 `Age` 屬性是[公用的](../../language-reference/keywords/public.md)，且同時包含 `get` 和 `set` 存取子。 這可讓任何物件讀取和寫入這些屬性。 但有時候會很想排除其中一個存取子。 例如，省略 `set` 存取子會讓屬性變成唯讀的：  
  
 [!code-csharp[properties#2](snippets/how-to-declare-and-use-read-write-properties/Program.cs#2)]
  
 或者，您也可以向公眾公開某個存取子，但讓其他存取子為私用或受保護的。 如需詳細資訊，請參閱[非對稱存取子的存取範圍](./restricting-accessor-accessibility.md)。  
  
 屬性一旦宣告，即可當成類別的欄位使用。 這在取得和設定屬性值時，可使用非常自然的語法，如下列陳述式所示：  
  
 [!code-csharp[properties#3](snippets/how-to-declare-and-use-read-write-properties/Program.cs#3)]
  
 請注意，在屬性 `set` 方法中提供特殊的 `value` 變數。 此變數包含使用者指定的值，例如：  
  
 [!code-csharp[properties#4](snippets/how-to-declare-and-use-read-write-properties/Program.cs#4)]
  
 請注意在 `Person` 物件上遞增 `Age` 屬性的全新語法：  
  
 [!code-csharp[properties#5](snippets/how-to-declare-and-use-read-write-properties/Program.cs#5)]
  
 如果分別使用 `set` 和 `get` 方法建立了屬性模型，對等的程式碼可能看起來像這樣：  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 本例中覆寫 `ToString` 方法：  
  
 [!code-csharp[properties#6](snippets/how-to-declare-and-use-read-write-properties/Program.cs#6)]
  
 請注意，程式中未明確使用 `ToString`。 預設會由 `WriteLine` 呼叫叫用。  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [屬性](./properties.md)
- [類別和結構](./index.md)
