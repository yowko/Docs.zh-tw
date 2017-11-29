---
title: "使用 WPF 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6fe8fb972f8080bbffeed5db2063d8c0484aec4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="using-wpf-controls"></a>使用 WPF 控制項
您可以在 Windows form 應用程式中使用 Windows Presentation Foundation (WPF) 控制項。 雖然這些是兩個不同的檢視技術，但是它們順暢的互通。  
  
 Windows Form 設計工具提供視覺化設計環境來裝載 Windows Presentation Foundation 控制項。 由名為特殊 Windows Form 控制項裝載 WPF 控制項<xref:System.Windows.Forms.Integration.ElementHost>。 這個控制項可讓 WPF 控制項加入表單的版面配置，並接收鍵盤和滑鼠的訊息。 您可以在設計階段排列<xref:System.Windows.Forms.Integration.ElementHost>控制就如同任何 Windows Form 控制項。  
  
 您也可以使用 Windows Form 控制項以 WPF 為基礎的應用程式中。 如需詳細資訊，請參閱[WPF 設計工具](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)。  
  
## <a name="in-this-section"></a>本章節內容  
 [操作說明：在設計階段複製和貼上 ElementHost 控制項](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 示範如何複製 Windows Form 上的 Windows Presentation Foundation 控制項。  
  
 [逐步解說：在設計階段排列 Windows Forms 的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何使用 Windows Form 的配置功能，例如錨定和對齊線，來排列 Windows Presentation Foundation 控制項。  
  
 [逐步解說：在設計階段變更已裝載之 WPF 元素的屬性](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 顯示 Windows Form 設計工具之間的工作流程和[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]變更 WPF 控制項的屬性。  
  
 [逐步解說：在設計階段建立 Windows Forms 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何建立使用 Windows Presentation Foundation 控制項在 Windows Form 為基礎的應用程式。  
  
 [逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 示範如何在 Windows Presentation Foundation 控制項複製到另一個 Windows Form。  
  
 [逐步解說：在設計階段指派 Windows Forms 的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 顯示如何選取您想要顯示在表單上的 Windows Presentation Foundation 控制項類型。  
  
 [逐步解說：設定 WPF 內容的樣式](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 顯示 Windows Form 設計工具之間的工作流程和[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]將樣式套用至 Windows Presentation Foundation 控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 描述您可以在 Windows form 應用程式中使用主機的 Windows Presentation Foundation 控制項的類別。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 描述您可以在 Windows Presentation Foundation 應用程式中使用主機的 Windows Form 控制項的類別。  
  
## <a name="related-sections"></a>相關章節  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 描述 Windows Presentation Foundation 和 Windows Form 技術之間的互通性。  
  
 [WPF 設計工具](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 描述如何設計中的 Windows Presentation Foundation 控制項[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。
