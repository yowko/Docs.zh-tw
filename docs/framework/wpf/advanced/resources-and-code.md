---
title: "資源和程式碼 | Microsoft Docs"
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
  - "索引鍵, 以物件做為"
  - "程序性程式碼, 存取資源"
  - "程序性程式碼, 建立資源"
  - "資源, 從程序性程式碼存取"
  - "資源, 以程序性程式碼建立"
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 資源和程式碼
本概觀著重於如何使用程式碼 \(而不是[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 語法\) 存取或建立 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資源。  如需從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法觀點了解一般資源用法和資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="accessing"></a>   
## 從程式碼存取資源  
 如果在程式碼中要求特定資源時，該資源是透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 定義，則也會用識別該資源的索引鍵來擷取該資源。  從程式碼中擷取資源最簡單的方式，就是從應用程式中的架構層級物件呼叫 <xref:System.Windows.FrameworkElement.FindResource%2A> 或 <xref:System.Windows.FrameworkElement.TryFindResource%2A> 方法。  這些方法表現出的行為差異在於找不到要求的索引鍵時的處理方式。  <xref:System.Windows.FrameworkElement.FindResource%2A> 會引發例外狀況，<xref:System.Windows.FrameworkElement.TryFindResource%2A> 不會引發例外狀況，但會傳回 `null`。  每個方法都會將資源索引鍵當做是輸入參數，並傳回不嚴格規定型別的物件。  資源索引鍵通常都是字串，但偶爾也會使用非字串，如需詳細資訊，請參閱[以物件做為索引鍵](#objectaskey)一節。  通常在要求資源時，您會將傳回的物件轉型為屬性需要的型別。  用於解析程式碼資源的查閱邏輯，與動態資源參考 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的情況一樣。  資源搜尋作業會先從發出呼叫的項目開始找，然後繼續往上找[邏輯樹狀結構](GTMT)中的父項目。  如果有需要，查閱會繼續尋找應用程式資源、主題和系統資源。  用於資源的程式碼要求將會適當說明資源字典中的執行階段變更 \(從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入資源字典後可能已經進行的變更\)，以及即時的系統資源變更。  
  
 以下這段簡短的程式碼範例會依索引鍵尋找資源，並用傳回的值來設定屬性，實作為 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式。  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 另一個指派資源參考的方法是 <xref:System.Windows.FrameworkElement.SetResourceReference%2A>。  這個方法會使用兩個參數：資源的索引鍵，以及項目執行個體上應該接收資源值之特殊相依性屬性的識別項。  這個方法在功能上是一樣的，但是有不必對傳回值進行任何轉型的優點。  
  
 以程式設計的方式存取資源還有另一個做法，就是將 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性的內容當做字典加以存取。  您也可以利用存取這個屬性包含之字典的方式，將新資源加入至現有集合、檢查集合中是否已有某個索引鍵名稱，和進行其他字典\/集合作業。  如果您要完全以程式碼撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，也可以用程式碼建立整個集合、指派索引鍵給集合，然後將完成後的集合指派給既有項目的 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性。  這些將會在下一節中說明。  
  
 您可以用特定索引鍵做為索引，在任何指定的 <xref:System.Windows.FrameworkElement.Resources%2A> 集合中建立索引，但您應該了解，以這種方式存取資源並不是遵守一般資源解析執行階段規則的作法。  您只是在存取那個特定的集合。  如果在要求的索引鍵找不到有效的物件，資源查閱作業的周遊範圍就不會擴大至根或應用程式。  但是，在某些情況下這個做法有效能上的優勢，因為搜尋索引鍵的範圍縮小了。  如需如何直接使用資源字典的詳細資訊，請參閱 <xref:System.Windows.ResourceDictionary> 類別。  
  
<a name="creating"></a>   
## 以程式碼建立資源  
 如果您要在程式碼中建立整個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，可能也會想以程式碼在這個應用程式中建立資源。  若要達成這個目的，請建立新的 <xref:System.Windows.ResourceDictionary> 執行個體，然後使用 <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> 呼叫，將所有資源加入至字典中。  接著，使用剛才建立的 <xref:System.Windows.ResourceDictionary> 來設定出現在頁面範圍中之項目的 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性，或是設定 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>。  您也可以將 <xref:System.Windows.ResourceDictionary> 當成獨立物件，而不將其加入至任何項目。  但是，如果您這麼做，就必須用項目索引鍵存取物件內的資源，就好像它是泛型字典一樣。  未附加至項目 `Resources` 屬性的 <xref:System.Windows.ResourceDictionary> 不會存在項目樹狀目錄中，而且在 <xref:System.Windows.FrameworkElement.FindResource%2A> 和相關方法可以使用的查閱順序中也不會有範圍。  
  
<a name="objectaskey"></a>   
## 以物件做為索引鍵  
 大多數資源用法會將資源的索引鍵設為字串。  但是，許多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能故意不使用字串型別來指定索引鍵，而是以物件做為這個參數。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 樣式和佈景主題支援會使用這類以物件當成資源索引鍵的功能。  佈景主題中每個要當成控制項 \(原本沒有樣式\) 預設樣式的樣式，都是以它們要套用至的控制項的 <xref:System.Type> 做為索引鍵。  以型別做為索引鍵提供了可信賴的查閱機制，這種機制只會在每種控制項型別的預設執行個體上查閱，而且型別可由反映 \(Reflection\) 偵測到，並且用來設定衍生類別 \(Derived Class\) 的樣式 \(儘管衍生型別原本沒有預設樣式\)。  您可以使用 [x:Type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)，替在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中定義的資源指定 <xref:System.Type> 索引鍵。  其他非字串索引鍵用法也有類似的延伸來支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，如 [ComponentResourceKey 標記延伸](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)。  
  
## 請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)