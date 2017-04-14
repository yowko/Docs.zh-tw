---
title: "在設計階段開發 Windows Form 控制項 | Microsoft Docs"
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
  - "Windows Form 控制項"
  - "建立的 Windows Form 控制項"
  - "控制項 [Windows Form]"
  - "建立控制項 [Windows Form]"
  - "使用者控制項 [Windows Form]"
  - "自訂控制項 [Windows Form]"
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 在設計階段開發 Windows Form 控制項
控制項作者的.NET Framework 提供豐富的控制項撰寫技術。 作者不再限於設計做為預先存在的控制項集合的複合控制項。 透過繼承，您可以從預先存在的複合控制項或預先存在的 Windows Form 控制項來建立您自己的控制項。 您也可以設計您自己實作自訂繪製的控制項。 這些選項可讓大量設計的彈性和功能的視覺介面。 若要利用這些功能，您應該熟悉以物件為基礎的程式設計概念。  
  
> [!NOTE]
>  不需要完全了解的繼承，但您可能會有用來參考[NOT IN 組建︰ 在 Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)。  
  
 如果您想要建立自訂控制項，以在 Web Form 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [逐步解說︰ 撰寫複合控制項與 Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 示範如何在 Visual Basic 中建立簡單的複合控制項。  
  
 [逐步解說︰ 撰寫複合控制項使用 Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 示範如何在 C# 中建立簡單的複合控制項。  
  
 [逐步解說︰ 繼承自使用 Visual Basic Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 示範如何建立簡單的 Windows Form 控制項，在 Visual Basic 中使用繼承。  
  
 [逐步解說︰ 繼承自使用 Visual C# Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 示範如何建立簡單的 Windows Form 控制項 C# 中使用繼承。  
  
 [逐步解說︰ 執行一般工作，使用智慧標籤在 Windows Form 控制項](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 示範如何使用 Windows Form 控制項的智慧標籤 」 功能。  
  
 [逐步解說︰ 序列化使用 designerserializationvisibilityattribute 序列化標準類型](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=fullName>序列化集合的屬性。  
  
 [逐步解說︰ 偵錯自訂的 Windows Form 控制項在設計階段](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 示範如何偵錯 Windows Form 控制項的設計階段行為。  
  
 [逐步解說︰ 建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 示範如何在設計環境緊密複合控制項。  
  
 [如何︰ 撰寫 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 提供實作 Windows Form 控制項的考量的概觀。  
  
 [如何︰ 撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 示範如何藉由繼承自複合控制項建立的控制項。  
  
 [如何︰ 繼承自 UserControl 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 建立複合控制項提供程序的概觀。  
  
 [如何︰ 繼承自現有的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 示範如何建立擴充的控制項，藉由繼承自<xref:System.Windows.Forms.Button>控制類別。  
  
 [如何︰ 繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 提供建立擴充的控制項的概觀。  
  
 [如何︰ 將控制項和表單邊緣對齊在設計階段](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 示範如何使用<xref:System.Windows.Forms.Control.Dock%2A>屬性，以符合您的控制項，會佔用的表單的邊緣。  
  
 [如何︰ 顯示在控制項選擇工具箱項目對話方塊](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 顯示安裝您的控制項，使其出現在程序**自訂工具箱**對話方塊。  
  
 [如何︰ 為控制項提供工具箱點陣圖](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 示範如何使用<xref:System.Drawing.ToolboxBitmapAttribute>顯示自訂控制項旁邊圖示**工具箱**。  
  
 [如何︰ 測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 示範如何使用**UserControl 測試容器**來測試複合控制項的行為。  
  
 [在 Windows Form 設計工具的設計階段錯誤](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 說明的意義與使用 Windows Form 設計工具載入失敗時，會出現在 Microsoft Visual Studio 設計階段錯誤清單。  
  
 [控制項和元件撰寫疑難排解](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 示範如何診斷和修正常見的問題可能是您撰寫自訂元件或控制項時。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control?displayProperty=fullName>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>  
 描述這個類別，並且提供其所有成員的連結。  
  
## <a name="related-sections"></a>相關章節  
 [使用.NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 討論如何使用.NET Framework 建立您自己的自訂控制項。  
  
 [語言獨立性以及與語言無關的元件](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 導入了 common language runtime，可簡化建立和使用的元件。 這個簡化的重要層面是使用不同的程式設計語言撰寫的元件之間的交互操作性增強。 Common Language Specification (CLS) 可讓您可以建立工具和處理多種程式設計語言的元件。  
  
 [逐步解說︰ 自動填入 [工具箱]，以自訂元件](../Topic/Walkthrough:%20Automatically%20Populating%20the%20Toolbox%20with%20Custom%20Components.md)  
 描述如何啟用您的元件或控制項中顯示**自訂工具箱**對話方塊。