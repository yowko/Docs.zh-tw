---
title: C# 保留屬性:條件屬性、過時屬性使用
ms.date: 04/09/2020
description: 這些屬性由編譯器解釋,以影響編譯器生成的代碼
ms.openlocfilehash: ca3b76387de2a57380d6eb0848991d979a558662
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389867"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>保留屬性:條件屬性、過時屬性、屬性使用屬性

這些屬性可以應用於代碼中的元素。 它們為這些元素添加語義意義。 編譯器使用這些語義含義來更改其輸出,並報告使用代碼的開發人員可能的錯誤。

## <a name="conditional-attribute"></a>`Conditional` 屬性

`Conditional` 屬性會根據前置處理識別碼來執行方法。 `Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。

在下面的範例中,`Conditional`應用於啟用或關閉程式的診斷資訊顯示的方法:

::::::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

如果未定義`TRACE_ON`識別碼,則不顯示追蹤輸出。 在互動式視窗中自行探索。

該`Conditional`屬性通常與識別碼一起`DEBUG`使用 ,用於為除錯產生啟用追蹤和紀錄記錄功能,但在發表版本中不使用,如以下範例所示:

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

當調用標記為條件的方法時,指定的預處理符號的存在或不存在將確定調用是包含還是省略。 如果定義符號，則會包括呼叫；否則會省略呼叫。 條件方法必須是類或結構聲明中的方法,並且必須具有`void`返回類型。 與`Conditional`將方法封閉在塊`#if…#endif`內 相比,使用更簡潔、更優雅、不易出錯。

如果方法有多個`Conditional`屬性,則如果定義了一個或多個條件符號(符號通過使用 OR 運算符以邏輯方式連結在一起),則包括對該方法的調用。 在下面的示例中,任一或`A``B`結果為方法調用:

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>使用`Conditional`屬性類別

`Conditional` 屬性也可以套用至屬性類別定義。 在下面的示例中,自定義屬性`Documentation`將僅向元數據添加資訊(`DEBUG`如果已定義)。

::::::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>`Obsolete` 屬性

該`Obsolete`屬性將代碼元素標記為不再建議使用。 使用標記為過時的實體會產生警告或錯誤。 `Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。 `Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。

在下面的範例中,`Obsolete`該屬性套用`A`於類別與`B.OldMethod`方法 。 因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。 不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。 例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰

::::::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

作為屬性建構函數的第一個參數提供的字串將顯示為警告或錯誤的一部分。 會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。 該`Obsolete`屬性無需參數即可使用,但建議說明使用什麼。

## <a name="attributeusage-attribute"></a>`AttributeUsage` 屬性

該`AttributeUsage`屬性確定如何使用自定義屬性類。 <xref:System.AttributeUsageAttribute> 是您套用至自訂屬性定義的屬性。 `AttributeUsage` 屬性可讓您控制：

- 屬性可能套用至哪些程式元素。 除非您限制其使用方式，否則屬性可能會套用至下列任一程式元素：
  - 組件 (assembly)
  - module
  - field
  - event
  - method
  - 參數
  - 屬性
  - return
  - type
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
