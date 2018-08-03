---
title: 撰寫自訂屬性
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114d24c1fc523d5501deb4aa17f9541c5a918276
ms.sourcegitcommit: 7fe772c6c05a982153655d618c826e9839d39cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "33574643"
---
# <a name="writing-custom-attributes"></a>撰寫自訂屬性
若要設計您自己的自訂屬性，並不需要精通很多新概念。 假如您擅長物件導向的程式設計，且瞭解如何設計類別，那麼您就已經擁有大部分所需的知識。 自訂屬性基本上是一種直接或間接衍生自 <xref:System.Attribute?displayProperty=nameWithType> 的傳統類別。 自訂屬性就像傳統類別一樣，含有儲存和擷取資料的方法。  
  
 正確設計自訂屬性的主要步驟如下：  
  
- [套用 AttributeUsageAttribute](#applying-the-attributeusageattribute)  
  
- [宣告屬性類別](#declaring-the-attribute-class)  
  
- [宣告建構函式](#declaring-constructors)  
  
- [宣告屬性](#declaring-properties)  
  
 本節會一一說明每個步驟，並於結尾提供 [自訂屬性範例](#custom-attribute-example)。  
  
## <a name="applying-the-attributeusageattribute"></a>套用 AttributeUsageAttribute  
 自訂屬性宣告的開頭為 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>，它定義您屬性類別的一些主要特性。 例如，您可以指定屬性是否可由其他類別繼承或指定屬性可以套用至哪一個項目。 下列程式碼片段示範如何使用 <xref:System.AttributeUsageAttribute>。  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute> 有三個建立自訂屬性所需的重要成員：[AttributeTargets](#attributetargets-member)、[Inherited](#inherited-property) 及 [AllowMultiple](#allowmultiple-property)。  
  
### <a name="attributetargets-member"></a>AttributeTargets 成員  
 在上述範例中，指定了 <xref:System.AttributeTargets.All?displayProperty=nameWithType> ，指出此屬性可以套用到所有程式元素。 或者，您也可以指定 <xref:System.AttributeTargets.Class?displayProperty=nameWithType>，指出您的屬性可以套用到類別，或指定 <xref:System.AttributeTargets.Method?displayProperty=nameWithType>，指出屬性只能套用至方法。 所有的程式項目都可以用這種方式透過自訂屬性標示為描述。  
  
 您也可以傳遞多個 <xref:System.AttributeTargets> 值。 下列程式碼片段指定自訂屬性可以套用至任何類別或方法。  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Inherited 屬性  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性會指出，衍生自套用您屬性之類別的類別，是否可繼承您的屬性。 此屬性會接受 `true` (預設值) 或 `false` 旗標。 在下列範例中，`MyAttribute` 的預設 <xref:System.AttributeUsageAttribute.Inherited%2A> 值為 `true`，而 `YourAttribute` 的 <xref:System.AttributeUsageAttribute.Inherited%2A> 值為 `false`。  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 兩個屬性接著會套用到基底類別 `MyClass` 中的方法。  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 最後，會從基底類別 `YourClass` 繼承類別 `MyClass`。 此方法 `MyMethod` 顯示 `MyAttribute`，但不是 `YourAttribute`。  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>AllowMultiple 屬性  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> 屬性會指出項目上是否可以有您屬性的多個執行個體。 如果設定為 `true`，則允許多個執行個體；如果設定為 `false` (預設值)，則只允許一個執行個體。  
  
 在下列範例中，`MyAttribute` 有預設的 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 值 `false`，而 `YourAttribute` 有 `true` 的值。  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 當套用這些屬性的多個執行個體時， `MyAttribute` 會產生編譯器錯誤。 下列程式碼範例示範有效的 `YourAttribute` 用法和無效的 `MyAttribute` 用法。  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 如果 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 屬性和 <xref:System.AttributeUsageAttribute.Inherited%2A> 屬性都設定為 `true`，繼承自另一個類別的類別可以繼承屬性，並在同一個子類別中套用同一屬性的另一個執行個體。 如果 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 設定為 `false`，父類別中任何屬性的值，都會被子類別中相同屬性的新執行個體覆寫。  
  
## <a name="declaring-the-attribute-class"></a>宣告屬性類別  
 在套用 <xref:System.AttributeUsageAttribute>之後，您可以開始定義屬性的細節。 如下列程式碼所示，屬性類別的宣告看起來類似傳統類別的宣告。  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 這個屬性的定義會顯示下列要點：  
  
- 屬性類別必須宣告為公用類別。  
  
- 依慣例，屬性類別的名稱會以這個字 **Attribute**結尾。 雖然並非必要，不過建議您遵照這個慣例以提高可讀性。 當屬性已套用時，要不要包含 Attribute 這個字都可以。  
  
- 所有的屬性類別必須直接或間接繼承自 <xref:System.Attribute?displayProperty=nameWithType>。  
  
- 在 Microsoft Visual Basic 中，所有自訂屬性的類別都必須有 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> 屬性。  
  
## <a name="declaring-constructors"></a>宣告建構函式  
 屬性使用建構函式進行初始化的方式，與傳統的類別相同。 下列程式碼片段說明典型的屬性建構函式。 這個公用建構函式會接受一個參數並將其值設定為等於成員變數。  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 您可以多載建構函式以容納不同的值組合。 如果您也為自訂的屬性類別定義[屬性](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) ，您可以在初始化屬性時使用具名和位置參數的組合。 通常您會將所有必要的參數定義為位置，而所有選擇性參數則定義為名稱。 在此情況下，屬性沒有必要的參數就無法初始化。 所有其他參數皆為選擇性使用。 請注意在 Visual Basic 中，屬性類別的建構函式不應使用 ParamArray 引數。  
  
 下列程式碼範例示範如何使用選擇性和必要的參數，來套用使用先前建構函示的屬性。 這項作業會假設屬性有一個必要的布林值和一個選擇性的字串屬性。  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>宣告屬性  
 如果您想要定義具名的參數或提供簡單的方式，來傳回屬性所儲存的值，請宣告 [屬性](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)。 屬性的屬性應該宣告為公用實體，並具有將傳回之資料類型的描述。 定義會保存您屬性值的變數，並將其與 **get** 和 **set** 方法建立關聯。 下列程式碼範例示範如何在您的屬性中實作簡單的屬性。  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>自訂屬性範例  
 本節包含先前的資訊，並說明如何設計簡單的屬性，記錄某一段程式碼的作者相關資訊。 此範例中的屬性儲存程式設計人員的名字和層級，以及此程式碼是否經過審閱。 它會使用三個私用變數來儲存要儲存的實際值。 每個變數都會以取得和設定值的公用屬性來表示。 最後，建構函式會以兩個必要參數來定義。  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 您可以用下列其中一種方式，也就是使用完整名稱 `DeveloperAttribute`，或使用縮寫名稱 `Developer`，來套用此屬性。  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 第一個範例示範只套用了必要具名參數的屬性，而第二個範例則示範同時套用了必要和選擇性參數的屬性。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>  
 [屬性](../../../docs/standard/attributes/index.md)
