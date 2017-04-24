---
title: "控制項 | Microsoft Docs"
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
  - "控制項 [WPF], 關於 WPF 控制項"
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 控制項
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 隨附許多幾乎每個 Windows 應用程式都會使用的常見 UI 元件，如 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.Menu> 和 <xref:System.Windows.Controls.ListBox>。  在過去，這些物件稱為控制項。  儘管 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK 仍會繼續使用「控制項」一詞來概括任何代表應用程式中可見物件的類別，但要注意，類別不必繼承自 <xref:System.Windows.Controls.Control> 類別，就可以顯現外觀。  繼承自 <xref:System.Windows.Controls.Control> 類別的類別會包含 <xref:System.Windows.Controls.ControlTemplate>，控制項的取用者可以用它將控制項的外觀完全改變，而不需要建立新的子類別 \(Subclass\)。  本主題討論在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中常見之控制項 \(包括繼承自和非繼承自 <xref:System.Windows.Controls.Control> 類別的控制項\) 的用法。  
  
   
  
<a name="creating_an_instance_of_a_control"></a>   
## 建立控制項的執行個體  
 您可以使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 或程式碼將控制項加入至應用程式。  下列範例顯示如何建立一個會詢問使用者姓氏和名字的簡單應用程式。  這個範例會在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中建立六個控制項：兩個標籤 \(Label\)、兩個文字方塊和兩個按鈕。  所有控制項的建立方式都類似。  
  
 [!code-xml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 下列範例會以程式碼建立相同的應用程式。  為求簡潔，範例中已經排除建立 <xref:System.Windows.Controls.Grid> `grid1` 的步驟。  `grid1` 具有與如前述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例所示的相同欄和列定義。  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## 變更控制項的外觀  
 變更控制項的外觀，使其更符合您應用程式的整體外觀及操作，這是很常見的。  您可以依據想要達成的效果，執行下列其中一項動作來變更控制項的外觀：  
  
-   變更控制項的屬性值。  
  
-   建立控制項的 <xref:System.Windows.Style>。  
  
-   建立控制項的新 <xref:System.Windows.Controls.ControlTemplate>。  
  
### 變更控制項的屬性值  
 許多控制項都有數個屬性可以用來變更控制項的外觀，如 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A>。  您可同時在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 以及程式碼中設定屬性的值。  下列範例會設定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中 <xref:System.Windows.Controls.Button> 上的 <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.FontSize%2A> 和<xref:System.Windows.Controls.Control.FontWeight%2A> 屬性。  
  
 [!code-xml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下列範例會以程式碼設定相同屬性。  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### 建立控制項的樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以讓您藉由建立 <xref:System.Windows.Style> 來指定整批控制項的外觀，而不必逐一設定應用程式中每一個執行個體的屬性。  下列範例建立的 <xref:System.Windows.Style> 會套用至應用程式中的每一個 <xref:System.Windows.Controls.Button>。<xref:System.Windows.Style> 的定義通常是在 <xref:System.Windows.ResourceDictionary> 中以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 定義，如 <xref:System.Windows.FrameworkElement> 的 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性。  
  
 [!code-xml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 您也可以將索引鍵指派給樣式，然後在控制項的 `Style` 屬性中指定該索引鍵，藉此只將樣式套用至特定型別的特定控制項。  如需樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
### 建立 ControlTemplate  
 <xref:System.Windows.Style> 可以讓您同時設定數個控制項的屬性，但有時候您想自訂的 <xref:System.Windows.Controls.Control> 外觀，可能就不是藉由建立 <xref:System.Windows.Style> 所能做到的。  繼承自 <xref:System.Windows.Controls.Control> 類別的類別會有 <xref:System.Windows.Controls.ControlTemplate>，可定義 <xref:System.Windows.Controls.Control> 的結構和外觀。  <xref:System.Windows.Controls.Control> 的 <xref:System.Windows.Controls.Control.Template%2A> 屬性是公用的，所以您可以給與 <xref:System.Windows.Controls.Control> 一個不同於其預設值的 <xref:System.Windows.Controls.ControlTemplate>。  您通常可以替 <xref:System.Windows.Controls.Control> 指定新的 <xref:System.Windows.Controls.ControlTemplate> 來自訂 <xref:System.Windows.Controls.Control> 的外觀，而不是繼承自控制項。  
  
 以最常用的控制項 <xref:System.Windows.Controls.Button> 為例。  <xref:System.Windows.Controls.Button> 的主要行為是在使用者按下它的時候讓應用程式做一些動作。  根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中出現的 <xref:System.Windows.Controls.Button> 是突起的矩形。  當您在開發應用程式時，可能會想利用 <xref:System.Windows.Controls.Button> 的行為 \(也就是處理按下按鈕的事件\)，但是想要變更按鈕的外觀，可是想要的外觀無法藉由變更按鈕的屬性來達到，  在這個情況下，您可以建立新的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 下列範例會建立 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.ControlTemplate>。  這個 <xref:System.Windows.Controls.ControlTemplate> 建立的 <xref:System.Windows.Controls.Button> 具有圓角和漸層背景。  <xref:System.Windows.Controls.ControlTemplate> 中包含 <xref:System.Windows.Controls.Border>，其 <xref:System.Windows.Controls.Border.Background%2A> 是具有兩個 <xref:System.Windows.Media.GradientStop> 物件的 <xref:System.Windows.Media.LinearGradientBrush>。  第一個 <xref:System.Windows.Media.GradientStop> 會以資料繫結方式將 <xref:System.Windows.Media.GradientStop> 的 <xref:System.Windows.Media.GradientStop.Color%2A> 屬性繫結至按鈕的背景色彩。  當您設定 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 屬性時，這個值的色彩就會做為第一個 <xref:System.Windows.Media.GradientStop>。  如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  這個範例也會建立 <xref:System.Windows.Trigger>，它會在 <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> 為 `true` 時變更 <xref:System.Windows.Controls.Button> 的外觀。  
  
 [!code-xml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 屬性必須設定為 <xref:System.Windows.Media.SolidColorBrush>，這個範例才能正常運作。  
  
<a name="subscribing_to_events"></a>   
## 訂閱事件  
 您可以使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼訂閱控制項的事件，但只能用程式碼處理事件。  下列範例顯示如何訂閱 <xref:System.Windows.Controls.Button> 的 `Click` 事件。  
  
 [!code-xml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下列範例會處理 <xref:System.Windows.Controls.Button> 的 `Click` 事件。  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## 擁有豐富內容的控制項  
 大部分繼承自 <xref:System.Windows.Controls.Control> 類別的類別都具有包含豐富內容的能力。  例如，<xref:System.Windows.Controls.Label> 可以包含任何物件，例如字串、<xref:System.Windows.Controls.Image> 或 <xref:System.Windows.Controls.Panel>。  下列類別可支援豐富內容，而且可做為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中大部分控制項的基底類別。  
  
-   <xref:System.Windows.Controls.ContentControl>\-\- <xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.ToolTip> 都是自這個類別繼承之類別的範例。  
  
-   <xref:System.Windows.Controls.ItemsControl>\-\- <xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.Menu> 和 <xref:System.Windows.Controls.Primitives.StatusBar> 都是自這個類別繼承之類別的範例。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>\-\- <xref:System.Windows.Controls.TabItem>、<xref:System.Windows.Controls.GroupBox> 和 <xref:System.Windows.Controls.Expander> 都是自這個類別繼承之類別的範例。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>\-\- <xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.TreeViewItem> 和 <xref:System.Windows.Controls.ToolBar> 都是自這個類別繼承之類別的範例。  
  
 如需這些基底類別庫的詳細資訊，請參閱 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [按分類區隔控制項](../../../../docs/framework/wpf/controls/controls-by-category.md)   
 [控制項程式庫](../../../../docs/framework/wpf/controls/control-library.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [輸入](../../../../docs/framework/wpf/advanced/input-wpf.md)   
 [啟用命令](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)   
 [逐步解說：建立自訂動畫按鈕](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)