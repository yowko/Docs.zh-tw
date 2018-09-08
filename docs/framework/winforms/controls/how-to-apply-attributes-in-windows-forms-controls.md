---
title: 如何：在 Windows Form 控制項中套用屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 1ab54b0c6828a0648fecfc293b6a7143b012ad6a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138561"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>如何：在 Windows Form 控制項中套用屬性
若要開發元件和控制項的設計環境中正確互動，並在執行階段會正確執行，您需要正確地將屬性套用至類別和成員。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用自訂控制項上的數個屬性。 控制項將示範簡單的記錄功能。 當控制項已繫結至資料來源時，它會顯示傳送中的資料來源的值<xref:System.Windows.Forms.DataGridView>控制項。 如果值超過所指定的值`Threshold`屬性，`ThresholdExceeded`就會引發事件。  
  
 `AttributesDemoControl`記錄值`LogEntry`類別。 `LogEntry`類別是範本類別，這表示它所記錄的型別上參數化。 例如，如果`AttributesDemoControl`是記錄值的型別`float`，每個`LogEntry`宣告執行個體，然後使用，如下所示。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  因為`LogEntry`已參數化的任意型別，它必須使用反映來操作參數型別。 閾值項功能就能運作，參數型別`T`必須實作<xref:System.IComparable>介面。  
  
 表單裝載`AttributesDemoControl`定期查詢的效能計數器。 每個值封裝在`LogEntry`適當的類型，並加入表單的<xref:System.Windows.Forms.BindingSource>。 `AttributesDemoControl`接收透過其資料繫結的值，並顯示在值<xref:System.Windows.Forms.DataGridView>控制項。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 第一個程式碼範例是`AttributesDemoControl`實作。 第二個程式碼範例示範如何使用的表單`AttributesDemoControl`。  
  
## <a name="class-level-attributes"></a>類別層級屬性  
 有些屬性被套用在類別層級。 下列程式碼範例會顯示通常會套用至 Windows Form 控制項的屬性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter 屬性  
 <xref:System.ComponentModel.TypeConverterAttribute> 是另一個常用的類別層級屬性。 下列程式碼範例示範使用`LogEntry`類別。 此範例也會示範實作<xref:System.ComponentModel.TypeConverter>for`LogEntry`型別，稱為`LogEntryTypeConverter`。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>成員層級屬性  
 有些屬性是在成員層級套用。 下列程式碼範例示範一些通常會套用到 Windows Form 控制項的屬性的屬性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue 屬性  
 下列範例示範<xref:System.ComponentModel.AmbientValueAttribute>而且顯示支援與設計環境互動的程式碼。 這種互動會呼叫*氣氛*。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>資料繫結屬性  
 下列範例示範複雜資料繫結的實作。 類別層級<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>、 顯示之前，指定`DataSource`和`DataMember`来用於資料繫結屬性。 <xref:System.ComponentModel.AttributeProviderAttribute>指定的型別`DataSource`屬性會繫結。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   裝載表單`AttributesDemoControl`需要參考`AttributesDemoControl`若要建置的組件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [使用 .NET Framework 開發自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [如何： 序列化標準類型使用 DesignerSerializationVisibilityAttribute 的集合](https://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
