---
title: .NET 的泛型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generic methods, type inference
- generics [.NET Framework], collections
- generic interfaces [.NET Framework]
- constructed generic types
- nested generic types
- generic type definitions
- generic classes [.NET Framework]
- generics [.NET Framework], interfaces
- generics [.NET Framework], about
- generics [.NET Framework]
- generic collections [.NET Framework]
- generic delegates [.NET Framework]
- generic type arguments
- generics [.NET Framework], delegates
- generics [.NET Framework], features
- constraints [.NET Framework]
- generic types
- generic type parameters
ms.assetid: 2994d786-c5c7-4666-ab23-4c83129fe39c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a4f4f3735c8952cf1458c63655eb56a82fd18f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666440"
---
# <a name="generics-in-net"></a>.NET 的泛型

<a name="top"></a> 泛型可讓您將方法、類別、結構或介面，修改成其發揮作用的精確資料類型。 例如，不使用 <xref:System.Collections.Hashtable> 類別，讓索引鍵和值可為任何類型；而改用 <xref:System.Collections.Generic.Dictionary%602> 泛型類別，指定索引鍵所允許的類型以及值所允許的類型。 泛型的優點包括加強程式碼的重複使用程度以及類型安全性。  
  
 本主題提供 .NET 中的泛型概觀，以及泛型類型或方法的摘要。 它包含以下各節：  
  
- [定義和使用泛型](#defining_and_using_generics)  
  
- [泛型術語](#generics_terminology)  
  
- [類別庫和語言支援](#class_library_and_language_support)  
  
- [巢狀類型和泛型](#nested_types_and_generics)  
  
- [相關主題](#related_topics)  
  
- [參考資料](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>定義和使用泛型  
 泛型是指一些類別、結構、介面與方法，其具有所儲存或使用之一或多個類型的預留位置 (類型參數)。 泛型集合類別可能會針對所儲存的物件類型，使用類型參數做為預留位置；這些類型參數會顯示為其欄位的類型，和其方法的參數類型。 泛型方法可能會使用其類型參數，做為其傳回值的類型，或其型式參數之一的類型。 下列程式碼將會示範簡單的泛型類別定義。  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 當您建立泛型類別的執行個體時，您會指定實際的類型來替代類型參數。 這會建立新的泛型類別，稱為建構的泛型類別，且在類型參數出現的任何地方，都有您所選擇的替代類型。 此結果是適合您選擇之類型的類型安全類別，如下程式碼所示。  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>泛型術語  
 下列詞彙會用於討論在 .NET 中的泛型：  
  
- *「泛型類型定義」* (generic type definition)，是做為範本的類別、結構或介面宣告，且具有可包含或使用之類型的預留位置。 例如， <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別可包含兩種類型：索引鍵和值。 因為泛型類型定義是只是範本，您無法建立泛型類型定義之類別、結構或介面的執行個體。  
  
- 「泛型型別參數」  或「型別參數」  ，是泛型型別或方法定義中的預留位置。 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 泛型類型有兩個類型參數， `TKey` 和 `TValue`，分別代表其索引鍵和值的類型。  
  
- *「建構的泛型類型」* (constructed generic type) 或 *「建構的類型」* (constructed type)，是為泛型類型定義的泛型類型參數所指定之類型的結果。  
  
- *「泛型類型引數」* (generic type argument) 是要替換泛型類型參數的所有類型。  
  
- 一般詞彙 *「泛型類型」* (generic type) 包括建構的類型和泛型類型定義。  
  
- 泛型型別參數的「共變數」  和「反變數」  可讓您使用建構的泛型型別，其型別引數比目標建構的型別有更多衍生 (共變數) 或更少衍生 (反變數)。 共變數和反變數合稱為「變異數」  。 如需詳細資訊，請參閱 [Covariance and Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md) (共變數和反變數)。  
  
- 「條件約束」  是對泛型型別參數的限制。 例如，您可以限制類型參數為實作 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 泛型介面的類型，以確保能夠排序類型的執行個體。 您也可以將型別參數限制為具有特定基底類別的型別，或是具有無參數建構函式的型別，或為參考型別或實值型別。 的泛型類型的使用者無法替換沒有滿足這些條件約束的類型引數。  
  
- *「泛型方法定義」* (generic method definition)，是一種有兩個參數清單的方法：泛型類型參數清單和型式參數清單。 類型參數會顯示為傳回類型或型式參數的類型，如下程式碼所示。  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 泛型方法可能會出現在泛型或非泛型類型上。 請務必注意，不會只因為某個方法屬於泛型類型，或只是因為它型式參數的類型是封入類型的泛用參數，此方法就成為泛型。 只有當方法有它自己的類型參數清單時，它才會是泛型。 在下列程式碼中，只有方法 `G` 是泛型。  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [回到頁首](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>泛型的優缺點  
 使用泛型集合和委派有許多優點：  
  
- 類型安全。 泛型會將類型安全的負擔轉移給編譯器。 並不需要撰寫程式碼以測試是否為正確的資料類型，因為它在編譯時期會強制執行。 降低了類型轉換的需求以及執行階段錯誤的可能性。  
  
- 程式碼較少且更容易重複使用程式碼。 沒有需要從基底類型繼承，並覆寫成員。 例如， <xref:System.Collections.Generic.LinkedList%601> 可以立即使用。 例如，您可以下列變數宣告，建立字串的連結清單：  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- 效能較佳。 泛型集合類型在儲存和管理實值類型上，通常有較好的表現，因為不需要 box 實值類型。  
  
- 泛型委派讓類型安全回呼不需要建立多個委派類別。 例如， <xref:System.Predicate%601> 泛型委派可讓您建立一種方法，為特定類型實作您自己的搜尋條件，以及讓您搭配 <xref:System.Array> 類型的方法 (例如 <xref:System.Array.Find%2A>、 <xref:System.Array.FindLast%2A>和 <xref:System.Array.FindAll%2A>) 使用方法。  
  
- 泛型簡化了動態產生的程式碼。 當您搭配動態產生的程式碼使用泛型時，不需要產生類型。 這會增加您使用輕量動態方法而非產生整個組件的時機。 如需詳細資訊，請參閱[如何：定義和執行動態方法](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) 與 <xref:System.Reflection.Emit.DynamicMethod>。  
  
 下列是泛型的一些限制：  
  
- 泛型類型可以從大部分的基底類別衍生，例如 <xref:System.MarshalByRefObject> (且可使用條件約束要求泛型類型參數衍生自基底類別，例如 <xref:System.MarshalByRefObject>)。 但 .NET Framework 不支援內容繫結的泛型型別。 泛型類型可以衍生自 <xref:System.ContextBoundObject>，但嘗試建立該類型的執行個體會導致 <xref:System.TypeLoadException>。  
  
- 列舉不能有泛型類型參數。 列舉只能偶爾做為泛型 (例如，因為它位於使用 Visual Basic、C# 或 C++ 所定義的泛型類型中)。 如需詳細資訊，請參閱 [Common Type System](../../../docs/standard/base-types/common-type-system.md)中的＜列舉＞。  
  
- 輕量動態方法不可為泛型。  
  
- 在 Visual Basic、C# 和 C++ 中，括在泛型類型中的巢狀類型無法具現化，除非已將指派給類型所有封入類型的類型參數。 另一個說法是，在反映中，已定義使用這些語言的巢狀類型，包括了其所有封入類型的類型參數。 這讓封入類型的類型參數，可用於巢狀類型的成員定義中。 如需詳細資訊，請參閱 <xref:System.Type.MakeGenericType%2A>中的「巢狀類型」。  
  
    > [!NOTE]
    >  透過發出動態組件中的程式碼或使用 [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) 所定義的巢狀型別，不一定要包含其封入型別的型別參數；不過，如果它不包含這些，型別參數就不在巢狀類別的範圍中。  
  
     如需詳細資訊，請參閱 <xref:System.Type.MakeGenericType%2A>中的「巢狀類型」。  
  
 [回到頁首](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>類別庫和語言支援  
 .NET 在下列命名空間中提供數個泛型集合類別：  
  
- <xref:System.Collections.Generic> 命名空間包含 .NET 所提供的大部分泛型集合類型，例如 <xref:System.Collections.Generic.List%601> 和 <xref:System.Collections.Generic.Dictionary%602> 泛型類別。  
  
- <xref:System.Collections.ObjectModel> 命名空間也包含其他泛型集合類型 (例如 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 泛型類別)，可用來向類別的使用者公開物件模型。  
  
 實作排序及相等比較的泛型介面，和事件處理常式、轉換及搜尋述詞的泛型委派類型，一起提供於 <xref:System> 命名空間中。  
  
 對泛型的支援已加入 <xref:System.Reflection> 命名空間，以檢查泛型類型和泛型方法；也加入 <xref:System.Reflection.Emit> ，以發出包含泛型類型和方法的動態組件；同時還加入 <xref:System.CodeDom> ，以產生包含泛型的來源圖形。  
  
 Common Language Runtime 提供新的 opcode 及前置詞，以支援 Microsoft 中繼語言 (MSIL) 中的泛型類型，包括 <xref:System.Reflection.Emit.OpCodes.Stelem>、 <xref:System.Reflection.Emit.OpCodes.Ldelem>、 <xref:System.Reflection.Emit.OpCodes.Unbox_Any>、 <xref:System.Reflection.Emit.OpCodes.Constrained>和 <xref:System.Reflection.Emit.OpCodes.Readonly>。  
  
 Visual C++、C# 和 Visual Basic 均提供定義及使用泛型的完整支援。 如需語言支援的詳細資訊，請參閱 [Visual Basic 中的泛型型別](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)、[泛型簡介](../../csharp/programming-guide/generics/index.md)和 [Visual C++ 中的泛型概觀](/cpp/windows/overview-of-generics-in-visual-cpp)。  
  
 [回到頁首](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>巢狀類型和泛型  
 泛型類型中的巢狀類型，可取決於封入泛型類型的類型參數。 Common Language Runtime 會將巢狀類型視為泛型，即使它們沒有自己的泛型類型參數。 當您建立巢狀類型的執行個體時，必須為所有封入泛型類型指定類型引數。  
  
 [回到頁首](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[.NET 中的泛型集合](../../../docs/standard/generics/collections.md)|描述 .NET 中的泛型集合類別以及其他泛型類型。|  
|[管理陣列和清單的泛型委派](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|描述轉換、搜尋述詞以及要在陣列或集合的元素上採取之動作的泛型委派。|  
|[泛型介面](../../../docs/standard/generics/interfaces.md)|描述提供泛型類型系列中常見功能的泛型介面。|  
|[共變數和反變數](../../../docs/standard/generics/covariance-and-contravariance.md)|描述泛型類型參數的共變數和反變數。|  
|[常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)|提供 .NET 中集合類型的特性和使用方式案例的摘要資訊，包括泛型類型。|  
|[何時使用泛型集合](../../../docs/standard/collections/when-to-use-generic-collections.md)|描述一般的規則，以判斷何時使用泛型集合類型。|  
|[如何：使用反映發出定義泛型型別](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|說明如何產生包括泛型類型和方法的動態組件。|  
|[Visual Basic 中的泛型型別](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|為 Visual Basic 使用者描述泛型功能，包括使用及定義泛型類型的「操作說明」主題。|  
|[泛型簡介](../../csharp/programming-guide/generics/index.md)|為 C# 使用者提供定義和使用泛型類型的概觀。|  
|[Visual C++ 中的泛型概觀](/cpp/windows/overview-of-generics-in-visual-cpp)|描述 C++ 使用者的泛型功能，包括泛型和範本之間的差異。|  
  
<a name="reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [回到頁首](#top)
