---
title: 在設計階段開發 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: b58318a3e0e9881725d3c260251288c720fa4132
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745107"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>在設計階段開發 Windows Form 控制項
針對控制項作者，.NET Framework 提供豐富的控制項撰寫技術。 作者不再只能設計作為預先存在之控制項集合的複合控制項。 透過繼承，您可以從預先存在的複合控制項或預先存在的 Windows Forms 控制項來建立自己的控制項。 您也可以設計可實作自訂繪製的專屬控制項。 這些選項可提供視覺介面設計和功能的大量彈性。 若要利用這些功能，您應該熟悉物件程式設計概念。  
  
> [!NOTE]
>  您不需要完全了解繼承，但您可能會有用來參考[繼承的基本概念 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果您想要建立自訂控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。  
  
## <a name="in-this-section"></a>本章節內容  
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 示範如何在 Visual Basic 中建立簡單的複合控制項。  
  
 [逐步解說：使用 Visual C# 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 示範如何在 C# 中建立簡單的複合控制項。  
  
 [逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 示範在 Visual Basic 中，如何使用繼承來建立簡單的 Windows Forms 控制項。  
  
 [逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 示範在 C# 中，如何使用繼承來建立簡單的 Windows Forms 控制項。  
  
 [逐步解說：使用 Windows Forms 控制項中的智慧標籤執行一般工作](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 示範如何在 Windows Forms 控制項上使用智慧標籤功能。  
  
 [逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType>來序列化集合的屬性。  
  
 [逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 示範如何偵錯 Windows Forms 控制項的設計階段行為。  
  
 [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 示範如何將複合控制項緊密整合至設計環境。  
  
 [操作說明：撰寫 Windows Forms 的控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 提供 Windows Forms 控制項實作考量的概觀。  
  
 [操作說明：撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 示範如何透過繼承自複合控制項來建立控制項。  
  
 [如何：繼承自 UserControl 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 提供如何建立複合控制項之程序的概觀。  
  
 [操作說明：繼承自現有的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 示範如何建立擴充的控制項，藉由繼承自<xref:System.Windows.Forms.Button>控制項類別。  
  
 [操作說明：繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 提供如何建立擴充控制項的概觀。  
  
 [操作說明：在設計階段將控制項對齊表單邊緣](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 示範如何使用<xref:System.Windows.Forms.Control.Dock%2A>屬性，以符合您的控制項，它會佔用表單的邊緣。  
  
 [操作說明：在選擇工具箱項目對話方塊中顯示控制項](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 示範如何安裝控制項的程序，讓它出現在 [自訂工具箱] 對話方塊中。  
  
 [操作說明：為控制項提供工具箱點陣圖](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 示範如何使用<xref:System.Drawing.ToolboxBitmapAttribute>若要在您的自訂控制項旁邊顯示圖示**工具箱**。  
  
 [操作說明：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 示範如何使用 [UserControl 測試容器] 來測試複合控制項的行為。  
  
 [Windows Forms 設計工具的設計階段錯誤](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 說明 Windows Forms 設計工具載入失敗時，Microsoft Visual Studio 中所出現的設計階段錯誤清單的意義與使用。  
  
 [針對控制項和元件撰寫進行疑難排解](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 示範如何診斷和修正在您撰寫自訂元件或控制項時可能發生的常見問題。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 描述這個類別，並且提供其所有成員的連結。  
  
## <a name="related-sections"></a>相關章節  
 [使用 .NET Framework 開發自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 討論如何使用 .NET Framework 建立您自己的自訂控制項。  
  
 [語言獨立性以及與語言無關的元件](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 介紹設計目的是要簡化元件建立和使用的 Common Language Runtime。 這個簡化的重要層面是使用不同程式設計語言所撰寫之元件之間增強的互通性。 Common Language Specification (CLS) 可讓您建立可處理多種程式設計語言的工具和元件。  
  
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 描述如何讓元件或控制項顯示在 [自訂工具箱] 對話方塊中。
