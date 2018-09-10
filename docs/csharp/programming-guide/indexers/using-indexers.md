---
title: 使用索引子 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 3e4c1f346b83cf97c57a359984bd08e075b6451b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253217"
---
# <a name="using-indexers-c-programming-guide"></a>使用索引子 (C# 程式設計手冊)
索引子是語法便利性，可讓您建立用戶端應用程式可以就像陣列一樣地存取的 [class](../../../csharp/language-reference/keywords/class.md)、[struct](../../../csharp/language-reference/keywords/struct.md) 或 [interface](../../../csharp/language-reference/keywords/interface.md)。 索引子最常實作於類型中，而類型的主要用途是封裝內部集合或陣列。 例如，假設您的 TempRecord 類別將華氏溫度代表為 24 小時期間記錄於 10 個不同的時間。 這個類別包含浮點類型的 "temps" 陣列以代表溫度，以及代表溫度記錄日期的 <xref:System.DateTime>。 在此類別中實作索引子，用戶端即可將 TempRecord 執行個體中的溫度存取為 `float temp = tr[4]`，而不是 `float temp = tr.temps[4]`。 索引子標記法不僅可簡化用戶端應用程式的語法，還可以讓其他開發人員更直覺地了解類別其用途。  
  
 若要在類別或結構上宣告索引子，請使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字，如此範例所示：  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a>備註  
 索引子類型和其參數類型至少必須可以像索引子本身一樣地存取。 如需存取範圍層級的詳細資訊，請參閱[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。  
  
 如需如何搭配使用索引子與介面的詳細資訊，請參閱[介面索引子](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)。  
  
 索引子的簽章包含其型式參數的數目和類型。 它不包含索引子類型或型式參數的名稱。 如果您在相同的類別中宣告多個索引子，則它們必須具有不同的簽章。  
  
 索引子值不會分類為變數；因此，您無法將索引子值傳遞為 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數。  
  
 若要提供具有其他語言可使用之名稱的索引子，請在宣告中使用 `name` 屬性。 例如:   
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 這個索引子的名稱會是 `TheItem`。 未提供名稱屬性會將 `Item` 設為預設名稱。  
  
## <a name="example-1"></a>範例 1  
  
### <a name="description"></a>描述  
 下列範例示範如何宣告私用陣列欄位 `temps` 和索引子。 索引子可讓您直接存取執行個體 `tempRecord[i]`。 使用索引子的替代方式是將陣列宣告為 [public](../../../csharp/language-reference/keywords/public.md) 成員，並直接存取其成員 `tempRecord.temps[i]`。  
  
 請注意，評估索引子的存取時 (例如，在 `Console.Write` 陳述式中)，會叫用 [get](../../../csharp/language-reference/keywords/get.md) 存取子。 因此，如果沒有 `get` 存取子，就會發生編譯時間錯誤。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>使用其他值編製索引  
 C# 不會將索引類型限制為整數。 例如，搭配使用字串與索引子可能十分有用。 在集合中搜尋字串，並傳回適當的值，可能會實作這類索引子。 多載存取子時，字串和整數版本可以共存。  
  
## <a name="example-2"></a>範例 2  
  
### <a name="description"></a>描述  
 在此範例中，宣告的類別會儲存週中的日。 宣告接受日名稱字串的 `get` 存取子，並傳回對應整數。 例如，星期日會傳回 0、星期一會傳回 1，依此類推。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 有兩種主要的方式可以改善索引子的安全性和可靠性：  
  
-   請務必包含某種類型的錯誤處理策略來處理用戶端程式碼傳入無效索引值的機會。 在本主題稍早的第一個範例中，TempRecord 類別提供 Length 屬性，以讓用戶端程式碼先確認輸入，再將其傳遞給索引子。 您也可以將錯誤處理程式碼放在索引子本身內。 請務必為使用者記載您在索引子存取子內擲回的任何例外狀況。  
  
-   將 `get` 和 [set](../../../csharp/language-reference/keywords/set.md) 存取子的存取範圍設定為合理限制。 這對 `set` 存取子特別重要。 如需詳細資訊，請參閱[限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [索引子](../../../csharp/programming-guide/indexers/index.md)  
- [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)
