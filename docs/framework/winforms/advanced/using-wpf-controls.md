---
title: 使用 WPF 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: be925bdceea3dd01c568d85fe025d6e037066454
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841599"
---
# <a name="using-wpf-controls"></a>使用 WPF 控制項
您可以在 Windows form 應用程式中使用 Windows Presentation Foundation (WPF) 控制項。 雖然這些都是兩個不同的檢視技術，它們順暢的互通。  
  
 Windows Form 設計工具提供視覺化設計環境來裝載 Windows Presentation Foundation 控制項。 由特殊的 Windows Form 控制項是名為裝載 WPF 控制項<xref:System.Windows.Forms.Integration.ElementHost>。 這個控制項可讓 WPF 控制項加入表單的版面配置，並接收鍵盤和滑鼠的訊息。 您可以在設計階段排列<xref:System.Windows.Forms.Integration.ElementHost>控制就如同任何 Windows Form 控制項。  
  
 您也可以在您以 WPF 為基礎的應用程式中使用 Windows Form 控制項。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)。  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：在設計階段複製和貼上 ElementHost 控制項](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 示範如何複製 Windows Form 上的 Windows Presentation Foundation 控制項。  
  
 [逐步解說：在設計階段排列 Windows Forms 的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何使用 Windows Form 的配置功能，例如錨定和對齊線，來排列 Windows Presentation Foundation 控制項。
  
 [逐步解說：在設計階段建立 Windows Forms 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何建立 Windows Presentation Foundation 控制項，以便在 Windows form 應用程式中。
  
 [逐步解說：在設計階段指派 Windows Forms 的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 顯示如何選取您想要在表單上顯示的 Windows Presentation Foundation 控制項類型。  
  
 [逐步解說：設定 WPF 內容的樣式](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 顯示 Windows Form 設計工具之間的工作流程和[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]將樣式套用至 Windows Presentation Foundation 控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 描述您可以在 Windows form 應用程式中使用來裝載 Windows Presentation Foundation 控制項的類別。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 描述您可以在 Windows Presentation Foundation 架構應用程式中使用來裝載 Windows Forms 控制項的類別。  
  
## <a name="related-sections"></a>相關章節  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 描述 Windows Presentation Foundation 和 Windows Form 技術之間的互通性。  
  
 [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)  
 描述如何設計 Visual Studio 中的 Windows Presentation Foundation 控制項。
