---
title: 'C # 保留屬性：條件式、已過時、AttributeUsage'
ms.date: 04/09/2020
description: 編譯器會解讀這些屬性來影響編譯器產生的程式碼
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2020
ms.locfileid: "82021772"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>保留屬性： ConditionalAttribute、ObsoleteAttribute、AttributeUsageAttribute

這些屬性可以套用至程式碼中的元素。 它們會將語義意義新增至這些元素。 編譯器會使用這些語義意義來改變其輸出，並在使用您的程式碼的開發人員報告可能的錯誤。

## <a name="conditional-attribute"></a>`Conditional` 屬性

`Conditional` 屬性會根據前置處理識別碼來執行方法。 `Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。

在下列範例中， `Conditional` 會套用至方法，以啟用或停用程式特定診斷資訊的顯示：

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

如果 `TRACE_ON` 未定義識別碼，則不會顯示追蹤輸出。 在互動式視窗中自行探索。

`Conditional`屬性通常會與識別碼搭配使用， `DEBUG` 以啟用 debug 組建的追蹤和記錄功能，而不是在發行組建中，如下列範例所示：

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

呼叫標記為條件的方法時，指定的前置處理符號是否存在或不存在，會決定是否要包含或省略呼叫。 如果定義符號，則會包括呼叫；否則會省略呼叫。 條件式方法必須是類別或結構宣告中的方法，而且必須有傳回 `void` 型別。 使用 `Conditional` 比區塊內的封入方法更簡潔、更簡潔、更不容易出錯 `#if…#endif` 。

如果某個方法具有多個 `Conditional` 屬性，則在定義一或多個條件式符號時，會包含方法的呼叫 (符號會以邏輯方式使用 or 運算子) 來連結在一起。 在下列範例中，或結果會出現 `A` `B` 在方法呼叫中：

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>搭配 `Conditional` 屬性類別使用

`Conditional` 屬性也可以套用至屬性類別定義。 在下列範例中，如果已定義，則自訂屬性 `Documentation` 只會將資訊新增至中繼資料 `DEBUG` 。

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>`Obsolete` 屬性

屬性會將 `Obsolete` 程式碼元素標示為不再建議使用。 使用標示為過時的實體會產生警告或錯誤。 `Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。 `Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。

在下列範例中， `Obsolete` 屬性會套用至類別 `A` 和方法 `B.OldMethod` 。 因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。 不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。 例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

以屬性函式的第一個引數提供的字串將會顯示為警告或錯誤的一部分。 會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。 `Obsolete`您可以使用不含引數的屬性，但建議您應改用的說明。

## <a name="attributeusage-attribute"></a>`AttributeUsage` 屬性

`AttributeUsage`屬性會決定自訂屬性類別的使用方式。 <xref:System.AttributeUsageAttribute> 是您套用至自訂屬性定義的屬性。 `AttributeUsage` 屬性可讓您控制：

- 屬性可能套用至哪些程式元素。 除非您限制其使用方式，否則屬性可能會套用至下列任一程式元素：
  - 組件
  - name
  - field
  - event
  - method
  - 參數
  - 屬性
  - return
  - 類型
- 屬性是否可以套用至單一程式元素多次。
- 衍生類別是否會繼承屬性。

明確套用時，預設設定看起來像下列範例：

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

在此範例中，`NewAttribute`　類別可套用至任何支援的程式元素。 但是，它只能套用至每個實體一次。 屬性在套用至基底類別時，會由衍生類別所繼承。

<xref:System.AttributeUsageAttribute.AllowMultiple> 和 <xref:System.AttributeUsageAttribute.Inherited> 是選擇性引數，因此下列程式碼具有相同的效果：

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

第一個 <xref:System.AttributeUsageAttribute> 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。 您可以使用 OR 運算子來連結多個目標類型，如下列範例所示：

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

從 C# 7.3 開始，屬性 (attribute) 可以套用至屬性 (property) 或自動實作屬性 (property) 的支援欄位。 除非您在屬性 (attribute) 上指定 `field` 指定名稱，否則屬性 (attribute) 會套用至屬性 (property)。 下列範例會顯示這兩者：

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

如果 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數為 `true`，則可以將產生的屬性多次套用至單一實體，如下列範例所示：

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttribute`。 套用多個屬性所顯示的兩種格式都有效。

如果 <xref:System.AttributeUsageAttribute.Inherited> 為 `false`，則衍生自屬性化類別的類別不會繼承此屬性。 例如：

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

在此情況下，不會透過繼承將 `NonInheritedAttribute` 套用至 `DClass`。

## <a name="see-also"></a>另請參閱

- <xref:System.Attribute>
- <xref:System.Reflection>
- [屬性](../../../standard/attributes/index.md)
- [反射](../../programming-guide/concepts/reflection.md)
