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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eebca72b8c564e6d846eba69b6b59139754738e
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015984"
---
# <a name="develop-windows-forms-controls-at-design-time"></a>在設計階段開發 Windows Forms 控制項

針對控制項作者，.NET Framework 提供豐富的控制項撰寫技術。 作者不再只能設計作為預先存在之控制項集合的複合控制項。 透過繼承，您可以從預先存在的複合控制項或預先存在的 Windows Forms 控制項來建立自己的控制項。 您也可以設計可實作自訂繪製的專屬控制項。 這些選項可提供視覺介面設計和功能的大量彈性。 若要利用這些功能，您應該熟悉物件程式設計概念。

> [!NOTE]
> 您不需要徹底瞭解繼承, 但您可能會發現參考[繼承基本概念 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)很有説明。

如果您想要建立自訂控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))。

## <a name="in-this-section"></a>本節內容

[逐步解說：撰寫複合控制項](walkthrough-authoring-a-composite-control-with-visual-csharp.md)\
示範如何在 C# 中建立簡單的複合控制項。

[逐步解說：繼承自 Windows Forms 控制項](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)\
示範在 C# 中，如何使用繼承來建立簡單的 Windows Forms 控制項。

[逐步解說：在 Windows Forms 控制項上使用智慧標籤執行一般工作](performing-common-tasks-using-smart-tags-on-wf-controls.md)\
示範如何在 Windows Forms 控制項上使用智慧標籤功能。

[逐步解說：使用 Designerserializationvisibilityattribute 序列化序列化標準類型的集合](serializing-collections-designerserializationvisibilityattribute.md)\
顯示如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType>屬性來序列化集合。

[逐步解說：在設計階段進行自訂 Windows Forms 控制項的調試](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)\
示範如何偵錯 Windows Forms 控制項的設計階段行為。

[逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項](creating-a-wf-control-design-time-features.md)\
示範如何將複合控制項緊密整合至設計環境。

[如何：Windows Forms 的作者控制項](how-to-author-controls-for-windows-forms.md)\
提供 Windows Forms 控制項實作考量的概觀。

[如何：撰寫複合控制項](how-to-author-composite-controls.md)\
示範如何透過繼承自複合控制項來建立控制項。

[如何：繼承自 UserControl 類別](how-to-inherit-from-the-usercontrol-class.md)\
提供如何建立複合控制項之程序的概觀。

[如何：繼承自現有的 Windows Forms 控制項](how-to-inherit-from-existing-windows-forms-controls.md)\
示範如何透過繼承自<xref:System.Windows.Forms.Button>控制項類別來建立擴充控制項。

[如何：繼承自控制項類別](how-to-inherit-from-the-control-class.md)\
提供如何建立擴充控制項的概觀。

[如何：在設計階段將控制項對齊表單邊緣](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)\
示範如何使用<xref:System.Windows.Forms.Control.Dock%2A>屬性, 將您的控制項對齊它所佔用表單的邊緣。

[如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)\
示範如何安裝控制項的程序，讓它出現在 [自訂工具箱] 對話方塊中。

[如何：提供控制項的工具箱點陣圖](how-to-provide-a-toolbox-bitmap-for-a-control.md)\
示範如何使用<xref:System.Drawing.ToolboxBitmapAttribute> , 在 [**工具箱**] 中顯示自訂控制項旁邊的圖示。

[如何：測試 UserControl 的執行時間行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)\
示範如何使用 [UserControl 測試容器] 來測試複合控制項的行為。

[Windows Forms 設計工具的設計階段錯誤](design-time-errors-in-the-windows-forms-designer.md)\
說明 Windows Forms 設計工具載入失敗時，Microsoft Visual Studio 中所出現的設計階段錯誤清單的意義與使用。

[針對控制項和元件撰寫進行疑難排解](troubleshooting-control-and-component-authoring.md)\
示範如何診斷和修正在您撰寫自訂元件或控制項時可能發生的常見問題。

## <a name="reference"></a>參考資料

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a>相關章節

[使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)\
討論如何使用 .NET Framework 建立您自己的自訂控制項。

[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)\
介紹設計目的是要簡化元件建立和使用的 Common Language Runtime。 這個簡化的重要層面是使用不同程式設計語言所撰寫之元件之間增強的互通性。 Common Language Specification (CLS) 可讓您建立可處理多種程式設計語言的工具和元件。

[逐步解說：使用自訂群組件自動填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)\
描述如何讓元件或控制項顯示在 [自訂工具箱] 對話方塊中。
