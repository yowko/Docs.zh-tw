---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 081a8f6edcddd5e87d3d9750b91ff42a72b92886
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656345"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

決定如何使用自訂屬性類別。 <xref:System.AttributeUsageAttribute> 是您套用至自訂屬性定義的屬性。 `AttributeUsage` 屬性可讓您控制：

- 屬性可能套用至哪些程式元素。 除非您限制其使用方式，否則屬性可能會套用至下列任一程式元素：
  - 組件
  - name
  - Field - 欄位
  - Event - 事件
  - 方法
  - param
  - 屬性
  - return
  - 類型
- 屬性是否可以套用至單一程式元素多次。
- 衍生類別是否會繼承屬性。

明確套用時，預設設定看起來像下列範例：

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

在此範例中，`NewAttribute`　類別可套用至任何支援的程式元素。 但是，它只能套用至每個實體一次。 屬性在套用至基底類別時，會由衍生類別所繼承。

<xref:System.AttributeUsageAttribute.AllowMultiple> 和 <xref:System.AttributeUsageAttribute.Inherited> 是選擇性引數，因此下列程式碼具有相同的效果：

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

第一個 <xref:System.AttributeUsageAttribute> 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。 您可以使用 OR 運算子來連結多個目標類型，如下列範例所示：

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

從 C# 7.3 開始，屬性 (attribute) 可以套用至屬性 (property) 或自動實作屬性 (property) 的支援欄位。 除非您在屬性 (attribute) 上指定 `field` 指定名稱，否則屬性 (attribute) 會套用至屬性 (property)。 下列範例會顯示這兩者：

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

如果 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數為 `true`，則可以將產生的屬性多次套用至單一實體，如下列範例所示：

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttribute`。 套用多個屬性所顯示的兩種格式都有效。

如果 <xref:System.AttributeUsageAttribute.Inherited> 為 `false`，則衍生自屬性化類別的類別不會繼承此屬性。 例如：

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

在此情況下，不會透過繼承將 `NonInheritedAttribute` 套用至 `DClass`。

## <a name="remarks"></a>備註

`AttributeUsage` 屬性是單次使用的屬性--它無法多次套用至相同的類別。 `AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的別名。

如需詳細資訊，請參閱[使用反映存取屬性 (C#)](accessing-attributes-by-using-reflection.md)。

## <a name="example"></a>範例

下列範例示範 <xref:System.AttributeUsageAttribute> 屬性的 <xref:System.AttributeUsageAttribute.Inherited> 和 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數的效果，以及如何列舉套用至類別的自訂屬性。

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a>範例輸出

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a>請參閱

- <xref:System.Attribute>  
- <xref:System.Reflection>  
- [C# 程式設計指南](../..//index.md)  
- [屬性](../../../..//standard/attributes/index.md)  
- [反映 (C#)](../reflection.md)  
- [屬性](index.md)  
- [建立自訂屬性 (C#)](creating-custom-attributes.md)  
- [使用反射存取屬性 (C#)](accessing-attributes-by-using-reflection.md)
