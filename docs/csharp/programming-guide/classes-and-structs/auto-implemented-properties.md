---
title: 自動實作的屬性 - C# 程式設計手冊
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 989266bfc2de9bd5ce2948f09a2b9f19dd2c782e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628289"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>自動實作的屬性 (C# 程式設計手冊)

在 C# 3.0 及更新版本中，當屬性存取子中不需要額外的邏輯時，自動實作的屬性可讓屬性宣告變得更精簡。 它們還可讓用戶端程式碼建立物件。 當您宣告屬性時，如下列範例所示，編譯器會建立私用、匿名的支援欄位，但只能透過屬性的 `get` 和 `set` 存取子才能存取。
  
## <a name="example"></a>範例

下列範例示範一個簡單的類別，其中包含一些自動實作的屬性：  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

您無法在介面中宣告自動實作為屬性。 自動執行的屬性會宣告私用實例支援欄位，而介面可能不會宣告實例欄位。 在介面中宣告屬性，而不定義主體，會宣告具有存取子的屬性，而必須由每個實作為介面的型別來執行。

在 C# 6 及更新版本中，您可以初始化自動實作的屬性，就像欄位一樣：  
 
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
 
先前範例中顯示的類別可變動。 用戶端程式代碼可以在建立之後變更物件中的值。 在包含重要行為（方法）和資料的複雜類別中，通常需要有公用屬性。 不過，對於只封裝一組值 (資料) 且只有很少甚至沒有行為的小型類別或結構，您應該將 set 存取子宣告為 [private](../../language-reference/keywords/private.md) (對取用者而言不可變)，或只宣告 get 存取子 (除了建構函式，在其他任何地方都不可變動)，將物件變成不可變動。  如需詳細資訊，請參閱[如何使用自動執行的屬性來執行輕量類別](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。

## <a name="see-also"></a>另請參閱

- [屬性](./properties.md)
- [修飾詞](/dotnet/csharp/language-reference/keywords)
