---
title: "自訂動畫概觀 | Microsoft Docs"
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
  - "動畫, 自訂類別"
  - "自訂動畫類別"
  - "自訂類別, 動畫"
  - "自訂主要畫面格"
  - "主要畫面格, 自訂"
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 自訂動畫概觀
本主題描述如何及何時藉由建立自訂主要畫面格、動畫類別，或使用單格回呼 \(Callback\) 予以略過，進而擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要條件  
 若要了解本主題，您應該熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的不同動畫型別。  如需詳細資訊，請參閱 [From\/To\/By 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)、[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)和[路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)。  
  
 由於動畫類別繼承自 <xref:System.Windows.Freezable> 類別，所以您應該熟悉 <xref:System.Windows.Freezable> 物件以及如何從 <xref:System.Windows.Freezable> 繼承。  如需詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="extendingtheanimationsystem"></a>   
## 擴充動畫系統  
 根據您要使用的內建功能層級而定，擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統的方法有很多種。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎中有三個主要擴充點：  
  
-   藉由從其中一個 *\<Type\>*KeyFrame 類別 \(例如 <xref:System.Windows.Media.Animation.DoubleKeyFrame>\) 繼承，建立自訂主要畫面格物件。  此方法會使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎的大部分內建功能。  
  
-   藉由從 <xref:System.Windows.Media.Animation.AnimationTimeline> 或其中一個 *\<Type\>*AnimationBase 類別繼承，建立自己的動畫類別。  
  
-   使用單格回呼，以單格方式產生動畫。  此方法會完全略過動畫和計時系統。  
  
 下表說明一些擴充動畫系統的案例。  
  
|當您要...|使用這個方法|  
|------------|------------|  
|在具有對應 *\<Type\>*AnimationUsingKeyFrames 之型別的值之間自訂插補|建立自訂主要畫面格。  如需詳細資訊，請參閱[建立自訂主要畫面格](#createacustomkeyframe)一節。|  
|在具有對應 *\<Type\>*Animation 之型別的值之間，自訂插補以外的功能|建立繼承自 *\<Type\>*AnimationBase 類別 \(此類別對應於您要以動畫顯示的型別\) 的自訂動畫類別。  如需詳細資訊，請參閱[建立自訂動畫類別](#createcustomanimationtype)一節。|  
|以動畫顯示沒有對應 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫的型別|使用 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 或建立繼承自 <xref:System.Windows.Media.Animation.AnimationTimeline> 的類別。  如需詳細資訊，請參閱[建立自訂動畫類別](#createcustomanimationtype)一節。|  
|使用每個畫面格都會計算而且以最後一組物件互動為基礎的值，以動畫顯示多個物件|使用單格回呼。  如需詳細資訊，請參閱[建立使用單格回呼](#useperframecallback)一節。|  
  
<a name="createacustomkeyframe"></a>   
## 建立自訂主要畫面格  
 建立自訂主要畫面格類別，是擴充動畫系統的最簡單方式。  當您要對主要畫面格動畫使用不同的插補方法時，請使用此方法。  如[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)所述，主要畫面格動畫使用主要畫面格物件來產生其輸出值。  每個主要畫面格物件可執行三項功能：  
  
-   使用其 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 屬性，指定目標值。  
  
-   使用其 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> 屬性，指定應達到該值的時間。  
  
-   實作 InterpolateValueCore 方法，在前一個主要畫面格的值與它自己的值之間進行插補。  
  
 **實作指示**  
  
 從 *\<Type\>*KeyFrame 抽象類別 \(Abstract Class\) 衍生，並實作 InterpolateValueCore 方法。  InterpolateValueCore 方法會傳回主要畫面格目前的值。  它會採用兩個參數：前一個主要畫面格的值和範圍從 0 到 1 的進度值。  進度為 0 表示主要畫面格才剛開始，而值為 1 則表示主要畫面格剛結束，而且應傳回其 <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> 屬性所指定的值。  
  
 因為 *\<Type\>*KeyFrame 類別繼承自 <xref:System.Windows.Freezable> 類別，所以您也必須覆寫 <xref:System.Windows.Freezable.CreateInstanceCore%2A> 核心，以便傳回新的類別執行個體。  如果此類別不使用[相依性屬性](GTMT)來儲存其資料，或者在建立之後需要額外進行初始化，您就必須覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 在您建立自訂 *\<Type\>*KeyFrame 動畫之後，您可以將它與該型別的 *\<Type\>*AnimationUsingKeyFrames 一起使用。  
  
<a name="createacustomanimationtype"></a>   
## 建立自訂動畫類別  
 建立您自己的動畫型別，讓您更能夠控制以動畫顯示物件的方式。  建立自己的動畫型別有兩種建議方法：您可以從 <xref:System.Windows.Media.Animation.AnimationTimeline> 類別或 *\<Type\>*AnimationBase 類別衍生。  但不建議從 *\<Type\>*Animation 或 *\<Type\>*AnimationUsingKeyFrames 類別衍生。  
  
### 從 \<Type\>AnimationBase 衍生  
 從 *\<Type\>*AnimationBase 類別衍生，是建立新動畫型別的最簡單方式。  當您要針對已經有對應 *\<Type\>*AnimationBase 類別的型別建立新動畫時，請使用此方法。  
  
 **實作指示**  
  
 從 *\<Type\>*Animation 類別衍生，並實作 GetCurrentValueCore 方法。  GetCurrentValueCore 方法會傳回動畫目前的值。  它會採用三個參數：建議的開始值、建議的結束值，以及用於判斷動畫進度的 <xref:System.Windows.Media.Animation.AnimationClock>。  
  
 因為 *\<Type\>*AnimationBase 類別繼承自 <xref:System.Windows.Freezable> 類別，所以您也必須覆寫 <xref:System.Windows.Freezable.CreateInstanceCore%2A> 核心，以便傳回新的類別執行個體。  如果此類別不使用[相依性屬性](GTMT)來儲存其資料，或者在建立之後需要額外進行初始化，您就必須覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 如需詳細資訊，請參閱 GetCurrentValueCore 方法文件中您要建立動畫之型別的 *\<Type\>*AnimationBase 類別。  如需範例，請參閱[自訂動畫範例](http://go.microsoft.com/fwlink/?LinkID=159981) \(英文\)  
  
 **替代方法**  
  
 如果您只想變更動畫值的插補方式，請考慮從其中一個 *\<Type\>*KeyFrame 類別衍生。  您所建立的主要畫面格可以搭配 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的對應 *\<Type\>*AnimationUsingKeyFrames 使用。  
  
### 從 AnimationTimeline 衍生  
 當您要針對尚未有對應 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫的型別建立動畫，或要建立不是強型別 \(Strongly Typed\) 的動畫時，請從 <xref:System.Windows.Media.Animation.AnimationTimeline> 類別衍生。  
  
 **實作指示**  
  
 從 <xref:System.Windows.Media.Animation.AnimationTimeline> 類別衍生並覆寫下列成員：  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> – 如果您的新類別是具象類別，則必須覆寫 <xref:System.Windows.Freezable.CreateInstanceCore%2A>，以傳回類別的新執行個體。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – 覆寫這個方法以傳回動畫的目前值。  它採用三個參數：預設起始值、預設目的值和 <xref:System.Windows.Media.Animation.AnimationClock>。  使用 <xref:System.Windows.Media.Animation.AnimationClock> 來取得動畫的目前時間或進度。  您可以選擇是否使用預設起始值和目的值。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – 覆寫這個屬性，以指出您的動畫是否使用由 <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> 方法指定的預設目的值。  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – 覆寫這個屬性，以指出您的動畫所產生之輸出的 <xref:System.Type>。  
  
 如果此類別不使用[相依性屬性](GTMT)來儲存其資料，或者在建立之後需要額外進行初始化，您就必須覆寫其他方法。如需詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 建議的開發架構 \(Paradigm\) \(由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫採用\) 就是使用兩個繼承 \(Inheritance\) 層級：  
  
1.  建立衍生自 <xref:System.Windows.Media.Animation.AnimationTimeline> 的抽象 *\<Type\>*AnimationBase 類別。  這個類別應該覆寫 <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> 方法。  它也應該會引入新的抽象方法 GetCurrentValueCore 並覆寫 <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>，以便驗證預設起始值和預設目的值參數的型別，然後再呼叫 GetCurrentValueCore。  
  
2.  建立另一個會繼承自新 *\<Type\>*AnimationBase 類別的類別，並覆寫 <xref:System.Windows.Freezable.CreateInstanceCore%2A> 方法、您引入的 GetCurrentValueCore 方法和 <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> 屬性。  
  
 **替代方法**  
  
 如果您要以動畫顯示沒有對應 From\/To\/By 動畫或主要畫面格動畫的型別，請考慮使用 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>。  因為它是弱型別，所以 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 可以以動畫顯示任何型別的值。  這個方法的缺點為 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 只支援[離散插補](GTMT)。  
  
<a name="useperframecallback"></a>   
## 使用單格回呼  
 當您需要完全略過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統時，請使用此方法。  此方法的其中一個案例就是物理動畫，其中的每個動畫步驟都需要根據最後一組物件互動而重新計算動畫物件的新方向或位置。  
  
 **實作指示**  
  
 與本概觀所描述的其他方法不同，若要使用單格回呼，您不必建立自訂動畫或主要畫面格類別。  
  
 您應改為註冊物件的 <xref:System.Windows.Media.CompositionTarget.Rendering> 事件，其中包含您要以動畫顯示的物件。  每個畫面格都會呼叫此事件處理常式方法一次。  每次 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將[視覺化樹狀結構](GTMT)中保留的呈現資料封送處理至複合樹狀結構，就會呼叫事件處理常式方法。  
  
 在事件處理常式中，執行動畫效果所需的所有計算，並設定您要用這些值來動畫顯示之物件的屬性。  
  
 若要取得目前畫面格的展示時間，可以將與此事件相關聯的 <xref:System.EventArgs> 轉型為 <xref:System.Windows.Media.RenderingEventArgs>，以提供您可用來取得目前畫面格呈現時間的 <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> 屬性。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Media.CompositionTarget.Rendering> 頁面。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.AnimationTimeline>   
 <xref:System.Windows.Media.Animation.IKeyFrame>   
 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [From\/To\/By 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [路徑動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [自訂動畫範例](http://go.microsoft.com/fwlink/?LinkID=159981)