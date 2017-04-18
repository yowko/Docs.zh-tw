---
title: "如何：在 Windows Form 控制項中套用屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "屬性 [Windows Form], 套用"
  - "控制項 [Windows Form], 套用屬性"
  - "Windows Form 控制項, 套用屬性"
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在 Windows Form 控制項中套用屬性
若要開發與設計環境正確互動、並在執行階段正確執行的元件和控制項，需要正確套用屬性至類別及成員。  
  
## 範例  
 下列程式碼範例示範如何在自訂控制項上使用數種屬性。  控制項示範簡單的記錄功能。  當控制項繫結至資料來源時，會顯示由 <xref:System.Windows.Forms.DataGridView> 控制項中資料來源所傳送的值。  如果值超過 `Threshold` 屬性所指定的值，便會引發 `ThresholdExceeded` 事件。  
  
 `AttributesDemoControl` 記錄具有 `LogEntry` 類別的值。  `LogEntry` 類別為樣板類別 \(Template Class\)，此類別會根據記錄的型別進行參數化。  例如，如果 `AttributesDemoControl` 記錄了 `float` 型別的值，就會宣告並使用每個 `LogEntry` 執行個體，如下所示：  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  因為 `LogEntry` 是依據任意的型別參數化，所以必須使用反映 \(Reflection\) 才能在參數型別上作業。  為了讓臨界值功能起作用，參數型別 `T` 必須實作 <xref:System.IComparable> 介面。  
  
 裝載 `AttributesDemoControl` 的表單會定期查詢效能計數器。  每個值都封裝於適當型別的 `LogEntry`，並加入至表單的 <xref:System.Windows.Forms.BindingSource>。  `AttributesDemoControl` 透過資料繫結接收值，並將值顯示於 <xref:System.Windows.Forms.DataGridView> 控制項中。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 第一個程式碼範例是 `AttributesDemoControl` 實作。  第二個程式碼範例示範使用 `AttributesDemoControl` 的表單。  
  
## 類別層級屬性  
 有些屬性 \(Attribute\) 是套用在類別層級。  下列程式碼範例示範常用來套用至 Windows Form 控制項的屬性。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### TypeConverter 屬性  
 <xref:System.ComponentModel.TypeConverterAttribute> 是另一種常用的類別層級屬性。  下列程式碼範例會示範 `LogEntry` 類別的用法。  這個範例也針對 `LogEntry` 型別示範了 <xref:System.ComponentModel.TypeConverter> 的實作，稱為 `LogEntryTypeConverter`。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## 成員層級屬性  
 有些屬性是套用在成員層級。  下列程式碼範例示範一些屬性 \(Attribute\)，這些屬性常套用至 Windows Form 控制項的屬性 \(Property\)。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### AmbientValue 屬性  
 下列程式碼範例示範 <xref:System.ComponentModel.AmbientValueAttribute>，並顯示支援與設計環境互動的程式碼。  這種互動稱為「*環境性*」\(Ambience\)。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### 資料繫結屬性  
 下列程式碼示範複雜資料繫結的實作。  先前所示的類別層級 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 會指定用做資料繫結的 `DataSource` 和 `DataMember` 屬性。  <xref:System.ComponentModel.AttributeProviderAttribute> 則會指定 `DataSource` 屬性將要繫結的型別。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## 編譯程式碼  
  
-   為了進行建置，裝載 `AttributesDemoControl` 的表單需要對 `AttributesDemoControl` 組件的參考。  
  
## 請參閱  
 <xref:System.IComparable>   
 <xref:System.Windows.Forms.DataGridView>   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)   
 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)