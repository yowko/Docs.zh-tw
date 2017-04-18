---
title: "逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項 | Microsoft Docs"
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
  - "複合控制項, 裝載 WPF"
  - "將 WPF 內容裝載在 Windows Form 中"
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項
本逐步解說會示範如何建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項，並使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項將它裝載 \(Host\) 於 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項和表單中。  
  
 在本逐步解說中，您會實作包含兩個子控制項的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。  <xref:System.Windows.Controls.UserControl> 會顯示立體 \(3\-D\) 圓錐體。  由於使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 呈現立體物件要比使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 來呈現簡單的多，  因此才會有在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 類別來建立立體圖形的這種做法。  
  
 逐步解說將說明的工作包括：  
  
-   建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。  
  
-   建立 Windows Form 主專案。  
  
-   裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[在 Windows Form 中裝載立體 WPF 複合控制項範例](http://go.microsoft.com/fwlink/?LinkID=160001) \(英文\)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## 建立使用者控制項  
  
#### 若要建立使用者控制項  
  
1.  建立 WPF 使用者控制項程式庫專案，並命名為 `HostingWpfUserControlInWf`。  
  
2.  在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]中開啟 UserControl1.xaml。  
  
3.  將產生的程式碼取代成下列程式碼：  
  
     這個程式碼會定義含有兩個子控制項的 <xref:System.Windows.Controls.UserControl?displayProperty=fullName>。  第一個子控制項是 <xref:System.Windows.Controls.Label?displayProperty=fullName> 控制項，第二個則是會顯示立體圓錐體的 <xref:System.Windows.Controls.Viewport3D> 控制項。  
  
     [!code-xml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## 建立 Windows Form 主專案  
  
#### 若要建立主專案  
  
1.  將名稱為 `WpfUserControlHost` 的 Windows 應用程式專案加入至方案。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/zh-tw/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
2.  在 \[方案總管\] 中，加入名為 WindowsFormsIntegration.dll 的 WindowsFormsIntegration 組件之參考。  
  
3.  加入下列 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件的參考：  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  加入 `HostingWpfUserControlInWf` 專案的參考。  
  
5.  在 \[方案總管\] 中，設定要做為啟始專案的 `WpfUserControlHost` 專案。  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## 裝載 Windows Presentation Foundation 使用者控制項  
  
#### 若要裝載使用者控制項  
  
1.  在 \[Windows Form 設計工具\] 中開啟 Form1。  
  
2.  在 \[屬性\] 視窗中按一下 \[**事件**\]，然後按兩下 <xref:System.Windows.Forms.Form.Load> 事件以建立事件處理常式。  
  
     \[程式碼編輯器\] 會開啟在新產生 `Form1_Load` 事件處理常式的地方。  
  
3.  將 Form1.cs 中的程式碼取代成下列程式碼。  
  
     `Form1_Load` 事件處理常式會建立 `UserControl1` 執行個體，並將它加入 `` <xref:System.Windows.Forms.Integration.ElementHost> 控制項的子控制項集合。  而 <xref:System.Windows.Forms.Integration.ElementHost> 控制項則會再加入至表單的子控制項集合。  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  按 F5 建置並執行應用程式。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [在 Windows Form 中裝載 WPF 複合控制項範例](http://go.microsoft.com/fwlink/?LinkID=160001)