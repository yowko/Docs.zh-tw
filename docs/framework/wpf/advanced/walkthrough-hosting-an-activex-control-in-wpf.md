---
title: "逐步解說：在 WPF 中裝載 ActiveX 控制項 | Microsoft Docs"
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
  - "ActiveX 控制項 [WPF 互通性]"
  - "裝載 ActiveX 控制項"
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# 逐步解說：在 WPF 中裝載 ActiveX 控制項
若要改善與瀏覽器的互動，可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式中使用 [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] 控制項。  本逐步解說示範如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 做為控制項。  
  
 逐步解說將說明的工作包括：  
  
-   建立專案。  
  
-   建立 ActiveX 控制項。  
  
-   將 ActiveX 控制項裝載於 WPF 頁面。  
  
 當您完成本逐步解說時，您將了解如何在您的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式中使用 [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] 控制項。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   在安裝 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 的電腦上安裝 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## 建立專案  
  
#### 若要建立並設定此專案  
  
1.  建立名稱為 `HostingAxInWpf` 的 WPF 應用程式專案。  
  
2.  將 Windows Form 控制項程式庫專案加入至方案，然後將專案命名為 `WmpAxLib`。  
  
3.  在 WmpAxLib 專案中，加入 Windows Media Player 組件 \(名為 wmp.dll\) 的參考。  
  
4.  開啟 \[**工具箱**\]。  
  
5.  以滑鼠右鍵按一下 \[**工具箱**\]，然後按一下 \[**選擇項目**\]。  
  
6.  按一下 \[**COM 元件**\] 索引標籤上的 \[**Windows Media Player**\] 控制項，然後按一下 \[**確定**\]。  
  
     Windows Media Player 控制項隨即加入至 \[**工具箱**\]。  
  
7.  以滑鼠右鍵按一下 \[方案總管\] 中的 \[**UserControl1**\] 檔案，然後按一下 \[**重新命名**\]。  
  
8.  將名稱變更為 `WmpAxControl.vb` 或 `WmpAxControl.cs` \(視語言而定\)。  
  
9. 如果出現替所有參考重新命名的提示，按一下 \[**是**\]。  
  
## 建立 ActiveX 控制項  
 當 [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] 控制項加入至設計介面時，[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 會自動產生控制項的 <xref:System.Windows.Forms.AxHost> 包裝函式類別 \(Wrapper Class\)。  下列程序會建立名為 AxInterop.WMPLib.dll 的 Managed 組件。  
  
#### 若要建立 ActiveX 控制項  
  
1.  在 \[Windows Form 設計工具\] 中開啟 WmpAxControl.vb 或 WmpAxControl.cs。  
  
2.  從 \[**工具箱**\] 將 Windows Media Player 控制項加入至設計介面。  
  
3.  在 \[屬性\] 視窗中，將 Windows Media Player 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值設定為 <xref:System.Windows.Forms.DockStyle>。  
  
4.  建置 WmpAxLib 控制項程式庫專案。  
  
## 將 ActiveX 控制項裝載於 WPF 頁面  
  
#### 若要裝載 ActiveX 控制項  
  
1.  在 HostingAxInWpf 專案中，加入產生之 [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] 互通性 \(Interoperability\) 組件的參考。  
  
     這個組件名為 AxInterop.WMPLib.dll，是在您當初匯入 Windows Media Player 控制項時，加入至 WmpAxLib 專案的 Debug 資料夾中。  
  
2.  加入 WindowsFormsIntegration 組件的參考，該組件名為 WindowsFormsIntegration.dll。  
  
3.  加入 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 組件的參考，該組件名為 System.Windows.Forms.dll。  
  
4.  在 \[WPF 設計工具\] 中開啟 MainWindow.xaml。  
  
5.  將 <xref:System.Windows.Controls.Grid> 項目命名為 `grid1`。  
  
     [!code-xml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  在 \[設計\] 檢視或 \[XAML\] 檢視中，選取 <xref:System.Windows.Window> 項目。  
  
7.  按一下 \[屬性\] 視窗中的 \[**事件**\] 索引標籤。  
  
8.  按兩下 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
9. 插入下列程式碼以處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
     此程式碼會建立 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的執行個體，並加入 `AxWindowsMediaPlayer` 控制項的執行個體做為其子系。  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. 按 F5 建置並執行應用程式。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)