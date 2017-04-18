---
title: "使用 WPF 控制項 | Microsoft Docs"
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
  - "互通性 [WPF]"
  - "Windows Form 設計工具, 與 WPF 的互通性"
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 使用 WPF 控制項
您可以在 Windows Form 架構應用程式中使用 Windows Presentation Foundation \(WPF\) 控制項。  雖然這是兩種不同的檢視技術，卻能夠平順地相互操作。  
  
 Windows Form 設計工具提供視覺化設計環境，用以裝載 Windows Presentation Foundation 控制項。  WPF 控制項是由名為 <xref:System.Windows.Forms.Integration.ElementHost> 的特殊 Windows Form 控制項所裝載。  這個控制項讓 WPF 控制項能夠參與表單的配置，並接收鍵盤與滑鼠訊息。  在設計階段，您可以用排列任何 Windows Form 控制項的方式來排列 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
 您也可以在 WPF 架構應用程式中使用 Windows Form 控制項。  如需詳細資訊，請參閱 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)。  
  
## 在本節中  
 [如何：在設計階段複製和貼上 ElementHost 控制項](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 示範如何複製 Windows Form 上的 Windows Presentation Foundation 控制項。  
  
 [逐步解說：在設計階段排列 Windows Form 的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何使用 Windows Form 配置功能 \(例如錨定和對齊線\) 排列 Windows Presentation Foundation 控制項。  
  
 [逐步解說：在設計階段變更已裝載之 WPF 項目的屬性](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 示範 Windows Form 設計工具與 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 之間變更 WPF 控制項屬性的工作流程。  
  
 [逐步解說：在設計階段建立 Windows Form 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何建立 Windows Presentation Foundation 控制項以便在 Windows Form 架構應用程式中使用。  
  
 [逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Form](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 示範如何將 Windows Presentation Foundation 控制項從某個 Windows Form 複製到另一個。  
  
 [逐步解說：在設計階段指派 Windows Form 的 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 示範如何選擇您要在表單上顯示的 Windows Presentation Foundation 控制項型別。  
  
 [逐步解說：設定 WPF 內容的樣式](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 示範 Windows Form 設計工具與 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 之間將樣式套用到 Windows Presentation Foundation 控制項的工作流程。  
  
## 參考  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 描述可以用來在 Windows Form 架構應用程式中裝載 Windows Presentation Foundation 控制項的類別。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 描述可以用來在 Windows Presentation Foundation 架構應用程式中裝載 Windows Form 控制項的類別。  
  
## 相關章節  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 描述 Windows Presentation Foundation 與 Windows Form 技術之間的互通性。  
  
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)  
 描述如何在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中設計 Windows Presentation Foundation 控制項。