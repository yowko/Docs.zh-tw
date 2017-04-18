---
title: "Windows Form 控制項中的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "屬性 [Windows Form]"
  - "屬性 [Windows Form], 類別"
  - "屬性 [Windows Form], 控制項屬性"
  - "屬性 [Windows Form], 資料繫結屬性"
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows Form 控制項中的屬性
.NET Framework 提供您可以套用至自訂控制項和元件之成員的各種屬性 \(Attribute\)。  這些屬性中，有些會影響類別的執行階段行為，其他的則會影響設計階段行為。  
  
## 控制項屬性 \(Attribute\) 和元件屬性 \(Property\)  
 下列資料表顯示您可以對自訂控制項和元件之屬性 \(Property\) 或其他成員所套用的屬性 \(Attribute\)。  如需使用多個屬性 \(Attribute\) 的使用範例，請參閱 [如何：在 Windows Form 控制項中套用屬性](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|指定要傳遞至屬性 \(Property\) 的值，該值會導致屬性取得來自另一個來源的值。  這稱為「*環境屬性*」\(Ambience Property\)。|  
|<xref:System.ComponentModel.BrowsableAttribute>|指定屬性 \(Property\) 或事件是否應該顯示於 \[**屬性**\] 視窗中。|  
|<xref:System.ComponentModel.CategoryAttribute>|當屬性或事件顯示在設定為 <xref:System.Windows.Forms.PropertySort> 模式的 <xref:System.Windows.Forms.PropertyGrid> 控制項中時，指定將屬性或事件分組的分類名稱。|  
|<xref:System.ComponentModel.DefaultValueAttribute>|指定屬性的預設值。|  
|<xref:System.ComponentModel.DescriptionAttribute>|指定屬性或事件的描述。|  
|<xref:System.ComponentModel.DisplayNameAttribute>|指定不需要任何引數的屬性、事件或 `public` `void` 方法的顯示名稱。|  
|<xref:System.ComponentModel.EditorAttribute>|指定用來變更屬性的編輯器。|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|指定在編輯器中可檢視的屬性或方法。|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|指定類別或成員的內容關鍵字。|  
|<xref:System.ComponentModel.LocalizableAttribute>|指定屬性是否應該當地語系化。|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|代表物件的文字表示由星號之類的字元所遮蔽。|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|指定這個屬性 \(Attribute\) 所繫結至的屬性 \(Property\) 在設計階段是否為唯讀，或可供讀取\/寫入。|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|表示在關聯的屬性 \(Property\) 值變更時，屬性方格應該重新整理。|  
|<xref:System.ComponentModel.TypeConverterAttribute>|指定要用來做為此屬性 \(Attribute\) 所繫結至物件的型別轉換子。|  
  
## 資料繫結屬性 \(Property\) 的屬性 \(Attribute\)  
 您可以套用下列資料表顯示的屬性 \(Attribute\)，以指定自訂控制項和元件與資料繫結互動的方式。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.ComponentModel.BindableAttribute>|指定屬性 \(Property\) 是否通常使用於繫結。|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|指定元件的資料來源和資料成員屬性。|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|指定元件的預設繫結屬性。|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|指定元件的資料來源和資料成員屬性。|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|啟用屬性 \(Attribute\) 重新導向。|  
  
## 類別的屬性 \(Attribute\)  
 您可以套用下列資料表顯示的屬性 \(Attribute\)，以指定自訂控制項和元件的行為。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|指定元件的預設事件。|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|指定元件的預設屬性。|  
|<xref:System.ComponentModel.DesignerAttribute>|指定用來實作元件的設計階段服務的類別。|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|指定屬於特定分類之類別的設計工具。|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|代表工具箱項目的屬性 \(Attribute\)。|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|指定使用於工具箱項目的篩選字串和篩選器類型。|  
  
## 請參閱  
 <xref:System.Attribute>   
 [如何：在 Windows Form 控制項中套用屬性](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)