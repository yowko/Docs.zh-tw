---
title: "反映和泛用類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 99d8da622b23a98b8a48ad6fcdb82c270d24ed22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reflection-and-generic-types"></a>反映和泛用類型
<a name="top"></a> 從反映的的觀點來看，泛型類型與一般類型間的差異在於泛型類型具有與其相關聯的一組類型參數 (若其定義為泛型類型) 或類型引數 (若其為建構類型)。 泛型方法與一般方法的差異也如同上述。  
  
 了解反映如何處理泛型類型和方法有兩種方式：  
  
-   <xref:System.Type> 類別的執行個體，代表泛型類型定義與泛型方法定義的類型參數。  
  
    > [!NOTE]
    >  <xref:System.Type> 物件代表泛型類型參數時，許多 <xref:System.Type> 的屬性與方法會有不同的行為。 這些差異皆記錄在屬性與方法主題中。 如需範例，請參閱 <xref:System.Type.IsAutoClass%2A> 與 <xref:System.Type.DeclaringType%2A>。 此外，部分成員僅限於 <xref:System.Type> 物件代表泛型類型參數時才有效。 如需範例，請參閱 <xref:System.Type.GetGenericTypeDefinition%2A>。  
  
-   如果 <xref:System.Type> 的執行個體代表泛型類型，則其包含一個代表類型參數 (若是泛型類型定義) 或代表類型引數 (若是建構類型) 的類型陣列。 上述同樣適用於代表泛型方法之 <xref:System.Reflection.MethodInfo> 類別的執行個體。  
  
 反映提供允許您存取類型參數陣列之 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo> 的方法，並決定 <xref:System.Type> 的執行個體是否代表類型參數或實際的類型。  
  
 如需示範此處所探論之方法的程式碼範例，請參閱[如何：使用反映檢視和執行個體化泛型型別](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)。  
  
 下列討論假設您熟悉泛型術語，例如類型參數與引數之間的差異，以及引數與開放式或封閉式的建構類型。 如需詳細資訊，請參閱[泛型](../../../docs/standard/generics/index.md)。  
  
 本概觀包含下列各節：  
  
-   [這是泛型類型或泛型方法？](#is_this_a_generic_type_or_method)  
  
-   [產生封閉式泛型類型](#generating_closed_generic_types)  
  
-   [檢查類型引數與類型參數](#examining_type_arguments)  
  
-   [非變異值](#invariants)  
  
-   [相關主題](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>這是泛型類型或泛型方法？  
 當您使用反映來查看未知的類型 (以 <xref:System.Type>的執行個體表示) 時，請使用 <xref:System.Type.IsGenericType%2A> 屬性來決定未知類型是否為泛型。 如果類型為泛型，其將傳回 `true` 。 同樣地，查看未知的方法 (以 <xref:System.Reflection.MethodInfo> 類別的執行個體表示) 時，請使用 <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> 屬性來決定方法是否為泛型。  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>這是泛型類型或方法定義？  
 使用 <xref:System.Type.IsGenericTypeDefinition%2A> 屬性來決定 <xref:System.Type> 物件是否代表泛型類型定義，並使用 <xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A> 方法來決定 <xref:System.Reflection.MethodInfo> 是否代表泛型方法定義。  
  
 泛型類型與方法定義為建立執行個體類型的範本。 .NET Framwork 類別庫中的泛型類型 (例如 <xref:System.Collections.Generic.Dictionary%602>) 是泛型類型定義。  
  
### <a name="is-the-type-or-method-open-or-closed"></a>類型 (或方法) 為開放式或是封閉式？  
 如果可具現化類型已取代其所有類型參數 (包括所有封入類型的類型參數)，則泛型類型或方法為封閉式。 如果類型為封閉式，則您僅能建立泛型類型的執行個體。 如果類型為開放式，則 <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> 屬性會傳回 `true` 。 若是方法，則 <xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A?displayProperty=nameWithType> 方法會執行相同的函式。  
  
 [回到頁首](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>產生封閉式泛型類型  
 若您有泛型類型或方法定義，使用 <xref:System.Type.MakeGenericType%2A> 方法可建立封閉式泛型類型，而使用 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> 方法則會為封閉式泛型方法建立 <xref:System.Reflection.MethodInfo> 。  
  
### <a name="getting-the-generic-type-or-method-definition"></a>取得泛型類型或方法定義  
 開放式類型或方法若不是泛型類型或方法定義，則無法建立該類型或方法的執行個體，且無法提供遺失的類型參數。 您必須具有泛型類型或泛型定義。 使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法可取得泛型類型定義，而使用 <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> 方法則可取得泛型方法定義。  
  
 例如，如果您有代表 <xref:System.Type> (在 Visual Basic 中為 `Dictionary<int, string>` ) 的`Dictionary(Of Integer, String)` 物件，而想要建立類型 `Dictionary<string, MyClass>`，可以使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法來取得代表 <xref:System.Type> 的 `Dictionary<TKey, TValue>` ，然後使用 <xref:System.Type.MakeGenericType%2A> 方法以產生代表 <xref:System.Type> 的 `Dictionary<int, MyClass>`。  
  
 以不是泛型類型的開放式泛型類型為例，請參閱本主題稍後的＜類型參數或類型引數＞。  
  
 [回到頁首](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>檢查類型引數與類型參數  
 使用 <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> 方法可取得代表泛型類型之類型參數或類型引數之 <xref:System.Type> 物件的陣列，若是泛型方法則請使用 <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> 方法以相同的方式取得陣列。  
  
 如果您已了解代表類型參數的 <xref:System.Type> 物件，則反映能夠回答許多額外的問題。 您可以決定類型參數的來源、其位置，及其條件約束。  
  
### <a name="type-parameter-or-type-argument"></a>類型參數或類型引數  
 若要判斷陣列的特定元素是類型參數或類型引數，請使用 <xref:System.Type.IsGenericParameter%2A> 屬性。 如果元素是類型參數，則 <xref:System.Type.IsGenericParameter%2A> 屬性為 `true` 。  
  
 泛型類型可以在不是泛型類型定義的情況下開啟，此時其具有類型引數和類型參數的混合。 以下列程式碼為例，類別 `D` 衍生自類型，該類型的第一個類型參數由 `D` 所取代，第二個類型參數則由 `B`取代。  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 如果您取得代表 <xref:System.Type> 的 `D<V, W>` 物件，並使用 <xref:System.Type.BaseType%2A> 屬性以取得其基底類型，所產生的 `type B<int, V>` 就會是開放式，但其不是泛型類型定義。  
  
### <a name="source-of-a-generic-parameter"></a>泛型參數的來源  
 泛型類型參數可能來自於目前正在檢查的類型、封入類型，或是來自泛型方法。 您可以透過下列方式來判斷泛型類型參數的來源：  
  
-   首先，使用 <xref:System.Type.DeclaringMethod%2A> 屬性來判斷類型參數是否來自泛型方法。 如果屬性值不是 null 參考 (在 Visual Basic 中為`Nothing` )，則來源為泛型方法。  
  
-   如果來源不是泛型方法，請使用 <xref:System.Type.DeclaringType%2A> 屬性來判斷泛型類型參數所屬的泛型類型。  
  
 如果類型參數屬於泛型的方法， <xref:System.Type.DeclaringType%2A> 屬性會傳回原先宣告泛型方法但不相關的類型。  
  
### <a name="position-of-a-generic-parameter"></a>泛型參數的位置  
 在很罕見的情況下，您必須判斷類型參數在類型參數清單中的宣告類別位置。 例如，假設您有前述範例中代表 <xref:System.Type> 類型的 `B<int, V>` 物件。 <xref:System.Type.GetGenericArguments%2A> 方法提供有類型引數的清單，且在查看 `V` 時，您可以使用 <xref:System.Type.DeclaringMethod%2A> 和 <xref:System.Type.DeclaringType%2A> 屬性以探索其來自何處。 您可以使用 <xref:System.Type.GenericParameterPosition%2A> 屬性來判斷其定義所在之類型參數清單中的位置。 在此範例中， `V` 位於其定義所在之類型參數清單中的位置 0 (零)。  
  
### <a name="base-type-and-interface-constraints"></a>基底類型與介面條件約束  
 使用 <xref:System.Type.GetGenericParameterConstraints%2A> 方法，以取得基底類型條件約束與類型參數的介面條件約束。 陣列元素的順序並不重要。 如果元素是介面類型，則該元素代表介面約束條件。  
  
### <a name="generic-parameter-attributes"></a>泛型參數屬性  
 <xref:System.Type.GenericParameterAttributes%2A> 屬性會取得表示變異數 (共變數或反變數) 及類型參數特殊條件約束的 <xref:System.Reflection.GenericParameterAttributes> 值。  
  
#### <a name="covariance-and-contravariance"></a>共變數和反變數  
 若要判斷類型參數是共變數或是反變數，請套用 <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> 遮罩至由 <xref:System.Reflection.GenericParameterAttributes> 屬性所傳回的 <xref:System.Type.GenericParameterAttributes%2A> 值。 如果結果為 <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>，則類型參數為非變異值。 請參閱 [共變數和反變數](../../../docs/standard/generics/covariance-and-contravariance.md)。  
  
#### <a name="special-constraints"></a>特殊條件約束  
 若要判斷類型參數的特殊條件約束，請套用 <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> 遮罩至 <xref:System.Reflection.GenericParameterAttributes> 屬性所傳回的 <xref:System.Type.GenericParameterAttributes%2A> 值。 如果結果是 <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>，則沒有特殊條件約束。 類型參數可以限制為參考類型、非 null 值類型，以及具有預設建構。  
  
 [回到頁首](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>非變異值  
 若要了解反映中泛型類型非變異條件hapi 一般條款表，請參閱 <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>。 與泛型方法相關的其他條款，請參閱 <xref:System.Reflection.MethodInfo.IsGenericMethod%2A?displayProperty=nameWithType>。  
  
 [回到頁首](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何：使用反映檢視和執行個體化泛型型別](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|示範如何使用 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo> 的屬性及方法，來檢查泛型類型。|  
|[泛型](../../../docs/standard/generics/index.md)|說明泛型功能，及在 .NET Framework 下如何加以支援。|  
|[操作說明：使用反映發出定義泛型型別](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|示範如何在動態組件中使用反映發出以產生泛型類型。|  
|[檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|描述 <xref:System.Type> 類別，並提供程式碼範例以說明如何搭配不同的反映類別來使用 <xref:System.Type>，以取得建構函式、方法、欄位、屬性與事件的相關資訊。|
