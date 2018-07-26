---
title: 屬性 (C# 程式設計手冊)
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 47f8e978d81b4aec94482f0a295691b830c3698c
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199156"
---
# <a name="properties-c-programming-guide"></a>屬性 (C# 程式設計手冊)

屬性是提供彈性機制以讀取、寫入或計算私用欄位值的成員。 使用屬性時可將其視為公用資料成員，但實際上屬性是名為「存取子」的特殊方法。 如此可讓資料更容易存取，同時有助於提升方法的安全性和彈性。  

## <a name="properties-overview"></a>屬性概觀  
  
- 屬性可讓類別公開取得和設定值的公用方式，同時隱藏實作或驗證程式碼。  
  
- [get](../../../csharp/language-reference/keywords/get.md) 屬性存取子可用來傳回屬性值，而 [set](../../../csharp/language-reference/keywords/set.md) 屬性存取子則用來指派新值。 這些存取子可以有不同的存取層級。 如需詳細資訊，請參閱[限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
- [value`set` 關鍵字是用來定義 ](../../../csharp/language-reference/keywords/value.md) 存取子要指派的值。  
- 屬性可以是「讀寫」(同時具有 `get` 和 `set` 存取子)、「唯讀」(具有 `get` 存取子但沒有 `set` 存取子) 或「唯寫」(具有 `set` 存取子但沒有 `get` 存取子)。 唯寫屬性很少見，而且最常用來限制對機密資料的存取。

- 不需要自訂存取子程式碼的簡單屬性，則可以實作為運算式主體定義或[自動實作屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。
 
## <a name="properties-with-backing-fields"></a>含有支援欄位的屬性

實作屬性的一種基本模式需要使用私用支援欄位，來設定和擷取屬性值。 `get` 存取子會傳回私用欄位的值，而 `set` 存取子則可能會執行一些資料驗證，再將值指派給私用欄位。 這兩個存取子也可能會對資料執行一些轉換或計算，再儲存或傳回資料。

下列範例將示範這個模式。 在此範例中，`TimePeriod` 類別代表時間間隔。 就內部而言，此類別會將時間間隔 (秒) 儲存在名為 `seconds` 的私用欄位中。 名為 `Hours` 的讀寫屬性可讓客戶以小時為單位指定時間間隔。 `get` 和 `set` 存取子都會執行小時與秒之間的必要轉換。 此外，`set` 存取子會驗證資料，並在小時數無效時擲回 <xref:System.ArgumentOutOfRangeException>。 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>運算式主體定義  

 屬性存取子通常是由只會指派或傳回運算式結果的單行陳述式所組成。 您可以將這些屬性實作為運算式主體成員。 運算式主體定義包含 `=>` 符號，後面接著要從屬性指派或擷取的運算式。

 從 C# 6 開始，唯讀屬性可將 `get` 存取子實作為運算式主體成員。 在此情況下，不會使用 `get` 存取子關鍵字和 `return` 關鍵字。 下列範例會將唯讀 `Name` 屬性實作為運算式主體成員。

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 從 C# 7.0 開始，可同時將 `get` 和 `set` 存取子實作為運算式主體成員。 在此情況下，必須同時有 `get` 和 `set` 關鍵字。 下列範例說明如何使用運算式主體定義來表示這兩個存取子。 請注意，`return` 關鍵字不能搭配 `get` 存取子使用。
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>自動實作屬性

在某些情況下，屬性 `get` 和 `set` 存取子只會指派值給支援欄位，或從支援欄位中擷取值，而不會包含任何其他邏輯。 藉由使用自動實作屬性，您可以簡化程式碼，同時讓 C# 編譯器無障礙地為您提供支援欄位。 

如果屬性具有 `get` 和 `set` 存取子，這兩者都必須自動實作。 您可以使用 `get` 和 `set` 關鍵字，但不提供任何實作，來定義自動實作屬性。 下列範例會重複上一個範例，不同之處在於 `Name` 和 `Price` 為自動實作屬性。 請注意，此範例也會移除參數化建構函式，讓 `SaleItem` 物件現在可透過呼叫預設建構函式和[物件初始設定式](object-and-collection-initializers.md)來進行初始化。

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>相關章節  
  
-   [使用屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [介面屬性](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [屬性與索引子之間的比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [使用屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [索引子](../../../csharp/programming-guide/indexers/index.md)  
 [get 關鍵字](../../../csharp/language-reference/keywords/get.md)    
 [set 關鍵字](../../../csharp/language-reference/keywords/set.md)    
