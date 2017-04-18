---
title: "逐步解說：使用 ElementHost 控制項對應屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ElementHost 控制項, 對應屬性"
  - "對應屬性"
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 逐步解說：使用 ElementHost 控制項對應屬性
本逐步解說顯示如何使用 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> 屬性將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 屬性對應至裝載之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目上的對應屬性。  
  
 逐步解說將說明的工作包括：  
  
-   建立專案。  
  
-   定義新的屬性對應。  
  
-   移除預設的屬性對應。  
  
-   擴充預設的屬性對應。  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[使用 ElementHost 控制項對應屬性範例](http://go.microsoft.com/fwlink/?LinkID=160018) \(英文\)。  
  
 完成時，就可以將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 屬性對應至裝載之項目上的對應 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## 建立專案  
  
#### 若要建立專案  
  
1.  建立 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式專案，取名為 `PropertyMappingWithElementHost`。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 \[方案總管\] 中加入下列 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件的參考。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  將下列程式碼複製至 `Form1` 程式碼檔案的最上面。  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  在 Windows Form 設計工具中開啟表單 `Form1`。  按兩下表單加入 <xref:System.Windows.Forms.Form.Load> 事件的事件處理常式。  
  
5.  回到 \[Windows Form 設計工具\]，並加入表單的 <xref:System.Windows.Forms.Control.Resize> 事件的事件處理常式。  如需詳細資訊，請參閱 [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/zh-tw/8461e9b8-14e8-406f-936e-3726732b23d2)。  
  
6.  在 `Form1` 類別中宣告 <xref:System.Windows.Forms.Integration.ElementHost> 欄位。  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## 定義新的屬性對應  
 <xref:System.Windows.Forms.Integration.ElementHost> 控制項會提供數個預設的屬性對應。  您可以藉由在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> 上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> 方法，加入新的屬性對應。  
  
#### 若要定義新的屬性對應  
  
1.  將下列程式碼複製到 `Form1` 類別的定義中。  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     `AddMarginMapping` 方法會加入 <xref:System.Windows.Forms.Control.Margin%2A> 屬性的新對應。  
  
     `OnMarginChange` 方法會將 <xref:System.Windows.Forms.Control.Margin%2A> 屬性轉譯成 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> 屬性。  
  
2.  將下列程式碼複製到 `Form1` 類別的定義中。  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     `AddRegionMapping` 方法會加入 <xref:System.Windows.Forms.Control.Region%2A> 屬性的新對應。  
  
     `OnRegionChange` 方法會將 <xref:System.Windows.Forms.Control.Region%2A> 屬性轉譯成 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> 屬性。  
  
     `Form1_Resize` 方法會處理表單的 <xref:System.Windows.Forms.Control.Resize> 事件，並且調整裁剪區域的大小以符合裝載的項目。  
  
## 移除預設的屬性對應  
 您可以藉由在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> 上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> 方法，移除預設的屬性對應。  
  
#### 若要移除預設的屬性對應  
  
-   將下列程式碼複製到 `Form1` 類別的定義中。  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     `RemoveCursorMapping` 方法會刪除 <xref:System.Windows.Forms.Control.Cursor%2A> 屬性的預設對應。  
  
## 擴充預設的屬性對應  
 您可以使用預設的屬性對應，同時以自己的對應加以擴充。  
  
#### 若要擴充預設的屬性對應  
  
-   將下列程式碼複製到 `Form1` 類別的定義中。  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     `ExtendBackColorMapping` 方法會將自訂屬性轉譯器加入至現有的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性對應。  
  
     `OnBackColorChange` 方法會將特定的影像指派至裝載之控制項的 <xref:System.Windows.Controls.Control.Background%2A> 屬性。  套用預設屬性對應之後，就會呼叫 `OnBackColorChange` 方法。  
  
## 初始化屬性對應  
  
#### 若要初始化屬性對應  
  
1.  將下列程式碼複製到 `Form1` 類別的定義中。  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     `Form1_Load` 方法會處理 <xref:System.Windows.Forms.Form.Load> 事件並執行下列初始化。  
  
    -   建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> 項目。  
  
    -   呼叫您稍早在這個逐步解說中定義的方法，以設定屬性對應。  
  
    -   將初始值指派給對應的屬性。  
  
2.  按 F5 建置並執行應用程式。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)