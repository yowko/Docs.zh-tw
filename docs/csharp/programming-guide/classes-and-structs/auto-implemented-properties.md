---
title: 自動實作的屬性 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 0d32dfd626cb8484e935dd0e8608c2e29d3ecbde
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45609745"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>自動實作的屬性 (C# 程式設計手冊)
在 C# 3.0 及更新版本中，當屬性存取子中不需要額外的邏輯時，自動實作的屬性可讓屬性宣告變得更精簡。 它們還可讓用戶端程式碼建立物件。 當您宣告屬性時，如下列範例所示，編譯器會建立私用、匿名的支援欄位，但只能透過屬性的 `get` 和 `set` 存取子才能存取。  
  
## <a name="example"></a>範例  
 下列範例示範一個簡單的類別，其中包含一些自動實作的屬性：  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 在 C# 6 及更新版本中，您可以初始化自動實作的屬性，就像欄位一樣：  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 先前範例中顯示的類別可變動。 用戶端程式碼可以在物件建立之後變更其中的值。 在包含重要行為 (方法) 和資料的複雜類別中，通常需要有公用屬性。 不過，對於只封裝一組值 (資料) 且只有很少甚至沒有行為的小型類別或結構，您應該將 set 存取子宣告為 [private](../../../csharp/language-reference/keywords/private.md) (對取用者而言不可變)，或只宣告 get 存取子 (除了建構函式，在其他任何地方都不可變動)，將物件變成不可變動。  如需詳細資訊，請參閱[如何：使用自動實作的屬性來實作輕量型類別](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。  
  
 自動實作的屬性 (Property) 上允許有屬性 (Attribute)，但在支援欄位上顯然不允許，因為從原始程式碼無法存取這些欄位。 如果您必須在屬性 (Property) 的支援欄位上使用屬性 (Attribute)，請建立一般屬性 (Property)。  
  
## <a name="see-also"></a>請參閱

- [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)
