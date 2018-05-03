---
title: 型別參數的條件約束 (C# 程式設計手冊)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25c4a1137df335080659bf878fce5e3a3270dfda
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>型別參數的條件約束 (C# 程式設計手冊)

條件約束會通知編譯器有關型別引數必須要有的功能。 如果沒有任何條件約束，則型別引數可以是任何型別。 編譯器只能採用 <xref:System.Object?displayPropety=nameWithType> 成員，這是任何 .NET 型別的最終基底類別。 如需詳細資訊，請參閱[為什麼使用條件約束](#why-use-constraints)。 如果用戶端程式碼嘗試使用條件約束不允許的類型來具現化類別，則結果是編譯時間錯誤。 條件約束是使用 `where` 內容關鍵字所指定。 下表列出七種類型的條件約束：

|條件約束|描述|
|----------------|-----------------|
|`where T: struct`|型別引數必須是實值型別。 您可以指定 <xref:System.Nullable> 以外的任何實值型別。 如需詳細資訊，請參閱[可為 Null 的型別](../nullable-types/using-nullable-types.md)。|
|`where T : class`|型別引數必須是參考型別。 此條件約束也適用於任何類別、介面、委派或陣列型別。|
|`where T : unmanaged`|型別引數不得是參考型別，也不得包含任何巢狀層級的任何參考型別成員。|
|`where T : new()`|型別引數必須有公用無參數建構函式。 與其他條件約束搭配使用時，`new()` 條件約束必須是最後一個指定的。|
|`where T :` *\<基底類別名稱>*|型別引數必須是或衍生自指定的基底類別。|
|`where T :` *\<介面名稱>*|型別引數必須是或實作指定的介面。 您可以指定多個介面條件約束。 條件約束介面也是泛型。|
|`where T : U`|針對 T 提供的型別引數必須是或衍生自針對 U 所提供的引數。|

有些條件約束會互斥。 所有實值型別都必須有可存取的無參數建構函式。 `struct` 條件約束表示 `new()` 條件約束和 `new()` 條件約束不能與 `struct` 條件約束合併使用。 `unmanaged` 條件約束表示 `struct` 條件約束。 `unmanaged` 條件約束不能與 `struct` 或 `new()` 條件約束合併使用。

## <a name="why-use-constraints"></a>為什麼使用條件約束

透過限制型別參數，即可增加條件約束類型和其繼承階層中所有類型所支援項目的允許作業和方法呼叫數目。 當您設計泛型類別或方法時，如果要對簡單指派以外的泛型成員執行任何作業，或呼叫 <xref:System.Object?displayProperty=nameWithType> 不支援的任何方法，則必須將條件約束套用至型別參數。 例如，基底類別條件約束會告知編譯器只有這個類型的物件或衍生自這個類型的物件才會用作型別引數。 編譯器具有這項保證之後，就可以允許在泛型類別中呼叫該類型的方法。 下列程式碼範例示範您可以套用基底類別條件約束來新增至 `GenericList<T>` 類別的功能 (在[泛型簡介](introduction-to-generics.md)中)。

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

條件約束可讓泛型類別使用 `Employee.Name` 屬性。 條件約束指定 `T` 型別的所有項目保證都是 `Employee` 物件或繼承自 `Employee` 的物件。

多個條件約束可以套用至相同的型別參數，而且條件約束本身可以是泛型型別，如下所示：

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

套用 `where T : class` 條件約束時，請避免在型別參數上使用 `==` 和 `!=` 運算子，因為這些運算子只會測試參考識別是否相等，但不會測試值是否相等。 即使在用作引數的型別中多載這些運算子，也會發生這種行為。 下列程式碼說明這點；輸出為 false，即使 <xref:System.String> 類別多載 `==` 運算子也是一樣。

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

編譯器在編譯時間只會知道 T 是參考型別，因此必須使用適用於所有參考型別的預設運算子。 如果您必須測試值是否相等，則建議同時套用 `where T : IEquatable<T>` 或 `where T : IComparable<T>` 條件約束，並在任何將用來建構泛型類別的類別中實作介面。

## <a name="constraining-multiple-parameters"></a>限制多個參數

您可以將條件約束套用至多個參數，以及將多個條件約束套用至單一參數，如下列範例所示：

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>未繫結的型別參數

 沒有條件約束的型別參數 (例如公用類別 `SampleClass<T>{}` 中的 T) 稱為「未繫結的型別參數」。 未繫結的型別參數具有下列規則：

- 因為不保證具體型別引數將支援 `!=` 和 `==` 運算子，所以無法使用這些運作子。
- 它們可以與 `System.Object` 進行來回轉換，或明確轉換成任何介面類型。
- 您可以將它們與 [Null](../../language-reference/keywords/null.md) 比較。 如果未繫結的參數與 `null` 進行比較，則型別引數是實值型別時，比較一律會傳回 false。

## <a name="type-parameters-as-constraints"></a>作為條件約束的型別參數

具有專屬型別參數的成員函式需要將該參數限制為包含類型的型別參數時，將泛型型別參數用作條件約束十分有用，如下列範例所示：

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

在上述範例中，`T` 是 `Add` 方法內容中的類型條件約束，以及 `List` 類別內容中的未繫結型別參數。

型別參數也可以在泛型類別定義中用作條件約束。 型別參數必須與任何其他型別參數一起宣告於角括弧內：

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

型別參數作為條件約束對泛型類別來說不實用，因為編譯器除了會假設型別參數衍生自 `System.Object` 之外，不會再做其他任何假設。 如果您要強制兩個型別參數之間具有繼承關係，請在泛型類別上將型別參數用作條件約束。

## <a name="unmanaged-constraint"></a>非受控條件約束

從 C# 7.3 開始，您可以使用 `unmanaged` 條件約束指定型別參數必須是「非受控型別」。 「非受控型別」是非參考型別的型別，而且未包含任何巢狀層級的參考型別欄位。 `unmanaged` 條件約束可讓您撰寫可重複使用的常式來使用型別，而型別可以操作為記憶體區塊，如下列範例所示：

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

上述方法必須在 `unsafe` 內容中進行編譯，因為它在不知道是內建型別的型別上使用 `sizeof` 運算子。 如果沒有 `unmanaged` 條件約束，則 `sizeof` 運算子無法使用。

## <a name="delegate-constraints"></a>委派條件約束

而且，從 C# 7.3 開始，您可以使用 <xref:System.Delegate?displayProperty=nameWithType> 或 <xref:System.MulticastDelegate?displayProperty=nameWithType> 作為基底類別條件約束。 CLR 一律允許這個條件約束，但 C# 語言不允許它。 `System.Delegate` 條件約束可讓您撰寫程式碼，以型別安全方式使用委派。 下列程式碼定義可結合兩個委派的擴充方法，但前提是它們的型別相同：

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

您可以使用上述方法來結合型別相同的委派：

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

如果您將最後一行取消註解，則不會編譯它。 `first` 和 `test` 都是委派型別，但它們是不同的委派型別。

## <a name="enum-constraints"></a>列舉條件約束

從 C# 7.3 開始，您也可以指定 <xref:System.Enum?displayProperty=nameWithType> 型別作為基底類別條件約束。 CLR 一律允許這個條件約束，但 C# 語言不允許它。 使用 `System.Enum` 的泛型提供型別安全程式設計，以快取在 `System.Enum` 中使用靜態方法的結果。 下列範例會尋找列舉型別的所有有效值，然後建置將這些值對應至其字串表示法的字典。

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

使用的方法會利用反映，而這會影響效能。 您可以呼叫這個方法來建置可快取和重複使用的集合，而不是重複需要反映的呼叫。

您可以如下列範例所示使用它來建立列舉，並建置其值和名稱的字典：

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>另請參閱

 <xref:System.Collections.Generic> [C# 程式設計手冊](../../../csharp/programming-guide/index.md)  
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)  
