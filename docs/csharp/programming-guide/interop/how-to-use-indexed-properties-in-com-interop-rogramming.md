---
title: 如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 5856ef871f865b2af0ab9ea637c26242cf99fb34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)
「索引的屬性」 改善具有參數的 COM 屬性在 C# 程式設計中的使用方式。 索引的屬性是與其他 Visual C# 功能 (例如[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)、新類型 ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)) 和[內嵌類型資訊](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)) 搭配運作，以加強 Microsoft Office 程式設計。  
  
 在舊版 C# 中，只有在 `get` 方法沒有參數以及 `set` 方法只有一個值參數時，才能將方法存取為屬性。 不過，並非所有 COM 屬性都符合這些限制。 例如，Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) 屬性具有需要範圍名稱參數的 `get` 存取子。 在過去，因為您無法直接存取 `Range` 屬性，所以必須改為使用 `get_Range` 方法，如下列範例所示。  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 索引的屬性可讓您改為撰寫下列程式碼︰  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  先前的範例也會使用[選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)功能，以讓您略過 `Type.Missing`。  
  
 與在 Visual C# 2008 和更早版本中設定 [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) 物件的 `Value` 屬性值類似，需要兩個引數。 其中一個提供選擇性參數的引數，而選擇性參數指定範圍值類型。 另一個則提供 `Value` 屬性的值。 下列範例說明這些技術。 兩個都將 A1 儲存格的值設定為 `Name`。
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 索引的屬性可讓您改為撰寫下列程式碼。  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 您無法建立自己本身的編製過索引的屬性。 這個功能僅支援使用現有已編製過索引的屬性。  
  
## <a name="example"></a>範例  
 下列程式碼顯示完整範例。 如需如何設定存取 Office API 之專案的詳細資訊，請參閱[如何：使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>請參閱  
 [具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [使用動態型別](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [如何：使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [逐步解說：Office 程式設計](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
