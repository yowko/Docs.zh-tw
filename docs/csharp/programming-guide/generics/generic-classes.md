---
title: 泛型類別 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 6eb4df4489f4b377c68c5d49d1bf0bb01b835e85
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589761"
---
# <a name="generic-classes-c-programming-guide"></a>泛型類別 (C# 程式設計手冊)
泛型類別會封裝不專屬於特定資料類型的作業。 泛型類別最常搭配類似連結清單、雜湊表、堆疊、佇列、樹狀結構等的集合。 無論儲存的資料類型為何，基本上是以相同的方式執行新增和移除集合項目等作業。  
  
 對需要集合類別的大多數案例而言，建議的方法是使用 .NET 類別庫中提供的那些類別。 如需使用這些類別的詳細資訊，請參閱 [.NET 中的泛型集合](../../../standard/generics/collections.md)。  
  
 建立泛型類別一般是從現有的實體類別開始，一次將一個類型變更成型別參數，直到達成一般化和可用性的最佳平衡。 在建立您自己的泛型類別時，重要考量包括：  
  
- 要將哪些類型一般化為型別參數。  
  
     依照規則，能夠參數化的類型愈多，程式碼就愈有彈性和可重複使用。 但是，過多的一般化，會建立讓其他開發人員不易閱讀或了解的程式碼。  
  
- 如果有的話，要將何種條件約束套用至型別參數 (請參閱[型別參數的條件約束](./constraints-on-type-parameters.md))。  
  
     理想的規則是盡可能套用最多的條件約束，卻仍能讓您處理必須處理的類型。 例如，如果您知道您的泛型類別，僅打算搭配參考型別，請套用類別條件約束。 這可防止類別非預期搭配實值型別，而且可讓您使用 `T` 的 `as` 運算子，並檢查 null 值。  
  
- 是否要將泛型行為分解成基底類別和子類別。  
  
     因為泛型類別可做為基底類別，所以這裡適用和非泛型類別相同的設計考量。 請參閱本主題稍後有關繼承自泛型基底類別的規則。  
  
- 是否要實作一或多個泛型介面。  
  
     例如，如果您要設計一個類別，用於建立泛型式集合的項目，您可能必須實作 `T` 是您類別類型的介面，例如 <xref:System.IComparable%601>。  
  
 如需簡單泛型類別的範例，請參閱[泛型簡介](./index.md)。  
  
 型別參數和條件約束的規則有數個泛型類別行為的含義，特別是有關繼承和成員存取範圍。 請先了解一些辭彙再繼續。 泛型類別 `Node<T>,` 用戶端程式碼可藉由指定型別引數來參考類別，建立封閉式的建構類型 (`Node<int>`)。 或者，它也可以保持不指定型別參數，例如，當您指定泛型基底類別時，建立開放式建構類型 (`Node<T>`)。 泛型類別可以繼承自實體、封閉式或開放式建構基底類別：  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 換言之，非泛型的實體類別可以繼承自封閉式建構基底類別，但不是繼承自開放式建構類別或型別參數，因為用戶端程式碼在執行階段沒有任何方法，提供必要的型別引數來具現化基底類別。  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 繼承自開放式建構類型的泛型類別必須為所有任何基底類別類型參數提供型別引數，而繼承類別不共用這些參數，如下列程式碼所示：  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 繼承自開放式建構類型的泛型類別必須指定條件約束，這些條件約束是基底類型上的條件約束超集，或暗示基底類型上的條件約束：  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 泛型型別可以使用多個型別參數和條件約束，如下所示：  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 開放式建構和封閉式建構類型可用為方法參數：  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 如果泛型類別實作某個介面，則該類別的所有執行個體都可以轉換成該介面。  
  
 泛型類別都是非變異值。 換句話說，如果輸入參數指定 `List<BaseClass>`，您會在嘗試提供 `List<DerivedClass>` 時收到編譯時期錯誤。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic>
- [C# 程式設計指南](../index.md)
- [泛型](./index.md)
- [Saving the State of Enumerators](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/) (儲存列舉程式狀態)
- [繼承謎題，第一部](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
