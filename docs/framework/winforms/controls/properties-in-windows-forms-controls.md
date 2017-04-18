---
title: "Windows Form 控制項中的屬性 | Microsoft Docs"
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
  - "控制項 [Windows Form], 屬性"
  - "自訂控制項 [Windows Form], 屬性概觀 (使用程式碼)"
  - "屬性 [Windows Form]"
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Windows Form 控制項中的屬性
Windows Form 控制項會從 <xref:System.Windows.Forms.Control?displayProperty=fullName> 基底類別繼承許多屬性。  這些屬性包括諸如 <xref:System.Windows.Forms.Control.Font%2A>、<xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Bounds%2A>、<xref:System.Windows.Forms.Control.ClientRectangle%2A>、<xref:System.Windows.Forms.Control.DisplayRectangle%2A>、<xref:System.Windows.Forms.Control.Enabled%2A>、<xref:System.Windows.Forms.Control.Focused%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A>、<xref:System.Windows.Forms.Control.Visible%2A>、<xref:System.Windows.Forms.Control.AutoSize%2A> 和其他許多屬性。  如需繼承屬性的詳細資訊，請參閱 <xref:System.Windows.Forms.Control?displayProperty=fullName>。  
  
 您可以在您的控制項中覆寫繼承的屬性，而且可以定義新屬性。  
  
## 在本節中  
 [定義屬性](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 示範如何實作自訂控制項或元件的屬性，並示範如何將屬性整合到設計環境中。  
  
 [使用 ShouldSerialize 和 Reset 方法定義預設值](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 示範如何定義自訂控制項或元件的預設屬性值。  
  
 [屬性變更事件](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 示範如何在屬性值變更時，啟用屬性變更告知。  
  
 [如何：公開組成控制項的屬性](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 示範如何在自訂的複合控制項中，公開組成控制項的屬性。  
  
 [自訂控制項中的方法實作](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 描述如何在自訂控制項和元件中實作方法。  
  
## 參考  
 <xref:System.Windows.Forms.UserControl>  
 提供實作複合控制項的基底類別的文件。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 提供指定 <xref:System.ComponentModel.TypeConverter> 以用於自訂屬性 \(Property\) 型別的屬性 \(Attribute\) 的文件。  
  
 <xref:System.ComponentModel.EditorAttribute>  
 提供指定 <xref:System.Drawing.Design.UITypeEditor> 以用於自訂屬性 \(Property\) 的屬性 \(Attribute\) 的文件。  
  
## 相關章節  
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 描述可以套用至自訂控制項和元件的屬性 \(Property\) 或其他成員的屬性 \(Attribute\)。  
  
 [元件的設計階段屬性](../Topic/Design-Time%20Attributes%20for%20Components.md)  
 列出套用於元件和控制項的中繼資料屬性 \(Metadata Attribute\)，以便它們在設計階段時於視覺設計工具正確顯示。  
  
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)  
 說明如何實作類別，例如提供設計階段支援的編輯器和設計工具。