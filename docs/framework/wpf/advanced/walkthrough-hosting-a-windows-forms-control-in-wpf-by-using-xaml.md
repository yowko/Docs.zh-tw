---
title: "逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "將 Windows Form 控制項裝載在 WPF 中"
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# 逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供許多具有豐富功能集的控制項。  但是，您有時候可能會想要在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  例如，您可能對現有的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項做了大筆投資，或擁有具備獨一無二功能的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
 本逐步解說顯示如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 \(Host\) Windows Form <xref:System.Windows.Forms.MaskedTextBox?displayProperty=fullName> 控制項。  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[使用 XAML 在 WPF 中裝載 Windows Form 控制項範例](http://go.microsoft.com/fwlink/?LinkID=160000) \(英文\)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## 裝載 Windows Form 控制項  
  
#### 若要裝載 MaskedTextBox 控制項  
  
1.  建立名稱為 `HostingWfInWpfWithXaml` 的 WPF 應用程式專案。  
  
2.  加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]中開啟 MainWindow.xaml。  
  
4.  在 <xref:System.Windows.Window> 項目中，加入下列命名空間對應。  `wf` 命名空間對應會建立組件的參考，這個組件包含 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  在 <xref:System.Windows.Controls.Grid> 項目中，加入下列 XAML。  
  
     <xref:System.Windows.Forms.MaskedTextBox> 控制項會建立為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的子系。  
  
     [!code-xml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  按 F5 建置並執行應用程式。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [逐步解說：在 WPF 中裝載 Windows Form 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Windows Form 控制項和對等 WPF 控制項](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)   
 [使用 XAML 在 WPF 中裝載 Windows Form 控制項範例](http://go.microsoft.com/fwlink/?LinkID=160000)