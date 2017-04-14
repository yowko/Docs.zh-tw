---
title: "如何：在設計階段複製和貼上 ElementHost 控制項 | Microsoft Docs"
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
  - "ElementHost 控制項, 在設計階段時複製與貼上"
  - "互通性 [WPF]"
  - "Windows Form, 內容複製及貼上"
  - "WPF 使用者控制項, 在 Windows Form 中裝載"
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在設計階段複製和貼上 ElementHost 控制項
本程序會示範如何複製 Windows Form 上的 Windows Presentation Foundation \(WPF\) 控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段複製和貼上 ElementHost 控制項  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 加入至您的 Windows Form 專案。  使用控制項型別的預設名稱 `UserControl1.xaml`。  如需詳細資訊，請參閱[逐步解說：在設計階段建立 Windows Form 的新 WPF 內容](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  在 \[**屬性**\] 視窗中，將 `UserControl1` 之 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的值設定為 `200`。  
  
3.  將 <xref:System.Windows.Controls.Control.Background%2A> 屬性的值設定為 `Blue`。  
  
4.  建置專案。  
  
5.  在 Windows Form 設計工具中開啟表單 `Form1`。  
  
6.  從 \[**工具箱**\] 將 `UserControl1` 的執行個體拖曳到表單上。  
  
     `UserControl1` 的執行個體裝載在名稱為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
7.  在選取 `elementHost1` 時，按 CTRL\+C 將其複製到剪貼簿。  
  
8.  按 CTRL\+V 將複製的控制項貼到表單上。  
  
     在表單上便會建立名為 `elementHost2` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Form](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)   
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)