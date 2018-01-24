---
title: "型別參數的條件約束 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f7c80acdb3815af4b5d545297894778029a9104
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>型別參數的條件約束 (C# 程式設計手冊)
當您定義泛型類別時，可以將限制套用至用戶端程式碼在具現化類別時可用於型別引數的類型種類。 如果用戶端程式碼嘗試使用條件約束不允許的類型來具現化類別，則結果是編譯時間錯誤。 這些限制稱為條件約束。 條件約束是使用 `where` 內容關鍵字所指定。 下表列出六種類型的條件約束：  
  
|條件約束|描述|  
|----------------|-----------------|  
|`where T: struct`|型別引數必須是實值型別。 您可以指定 <xref:System.Nullable> 以外的任何實值型別。 如需詳細資訊，請參閱[使用可為 Null 的類型](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)。|  
|`where T : class`|型別引數必須是參考型別；這也適用於任何類別、介面、委派或陣列類型。|  
|`where T : new()`|型別引數必須有公用無參數建構函式。 與其他條件約束搭配使用時，`new()` 條件約束必須是最後一個指定的。|  
|`where T : `\<基底類別名稱>|型別引數必須是或衍生自指定的基底類別。|  
|`where T : `\<介面名稱>|型別引數必須是或實作指定的介面。 您可以指定多個介面條件約束。 條件約束介面也是泛型。|  
|`where T : U`|針對 T 提供的型別引數必須是或衍生自針對 U 所提供的引數。|  
  
## <a name="why-use-constraints"></a>為什麼使用條件約束  
 如果您想要檢查泛型清單中的項目來判斷它是否有效，或比較它與某個其他項目，則編譯器必須保證用戶端程式碼所指定的任何型別引數將支援編譯器必須呼叫的運算子或方法。 這項保證是透過將一或多個條件約束套用至泛型類別定義來獲得。 例如，基底類別條件約束會告知編譯器只有這個類型的物件或衍生自這個類型的物件才會用作型別引數。 編譯器具有這項保證之後，就可以允許在泛型類別中呼叫該類型的方法。 條件約束是使用 `where` 內容關鍵字所套用。 下列程式碼範例示範我們可以套用基底類別條件約束來新增至 `GenericList<T>` 類別的功能 (在[泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)中)。  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 條件約束可讓泛型類別使用 `Employee.Name` 屬性，因為類型 T 的所有項目一定是 `Employee` 物件或是繼承自 `Employee` 的物件。  
  
 多個條件約束可以套用至相同的型別參數，而且條件約束本身可以是泛型型別，如下所示：  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 透過限制型別參數，即可增加條件約束類型和其繼承階層中所有類型所支援項目的允許作業和方法呼叫數目。 因此，當您設計泛型類別或方法時，如果要對簡單指派以外的泛型成員執行任何作業，或呼叫 `System.Object` 不支援的任何方法，則必須將條件約束套用至型別參數。  
  
 套用 `where T : class` 條件約束時，請避免在型別參數上使用 `==` 和 `!=` 運算子，因為這些運算子只會測試參考識別是否相等，但不會測試值是否相等。 這是這種情況，即使在用作引數的類型中多載這些運算子也是一樣。 下列程式碼說明這點；輸出為 false，即使 <xref:System.String> 類別多載 `==` 運算子也是一樣。  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 這項行為的原因在於，在編譯時間，編譯器只會知道 T 是參考型別，因此必須使用適用於所有參考型別的預設運算子。 如果您必須測試值是否相等，建議方式也會套用 `where T : IComparable<T>` 條件約束，並在任何將用來建構泛型類別的類別中實作該介面。  
  
## <a name="constraining-multiple-parameters"></a>限制多個參數  
 您可以將條件約束套用至多個參數，以及將多個條件約束套用至單一參數，如下列範例所示：  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a>未繫結的型別參數  
 沒有條件約束的型別參數 (例如公用類別 `SampleClass<T>{}` 中的 T) 稱為「未繫結的型別參數」。 未繫結的型別參數具有下列規則：  
  
-   因為不保證具體型別引數將支援 `!=` 和 `==` 運算子，所以無法使用這些運作子。  
  
-   它們可以與 `System.Object` 進行來回轉換，或明確轉換成任何介面類型。  
  
-   您可以比較 [null](../../../csharp/language-reference/keywords/null.md)。 如果未繫結的參數與 `null` 進行比較，則型別引數是實值型別時，比較一律會傳回 false。  
  
## <a name="type-parameters-as-constraints"></a>作為條件約束的型別參數  
 具有專屬型別參數的成員函式需要將該參數限制為包含類型的型別參數時，將泛型型別參數用作條件約束十分有用，如下列範例所示：  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 在上述範例中，`T` 是 `Add` 方法內容中的類型條件約束，以及 `List` 類別內容中的未繫結型別參數。  
  
 型別參數也可以在泛型類別定義中用作條件約束。 請注意，型別參數必須與任何其他型別參數一起宣告於角括弧內：  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 型別參數作為條件約束對泛型類別來說極不實用，因為編譯器除了會假設型別參數衍生自 `System.Object` 之外，不會再做其他任何假設。 如果您要強制兩個型別參數之間具有繼承關係，請在泛型類別上將型別參數用作條件約束。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Collections.Generic>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)
