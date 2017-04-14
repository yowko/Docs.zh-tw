---
title: "巡覽拓撲概觀 | Microsoft Docs"
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
  - "動態產生的拓撲"
  - "固定的階層式拓撲"
  - "固定線性拓撲"
  - "線性拓撲"
  - "巡覽拓撲 [WPF]"
  - "拓撲 [WPF]"
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 巡覽拓撲概觀
<a name="introduction"></a> 本概觀介紹 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的巡覽拓撲，  並接著討論三種常見的巡覽拓撲及其範例。  
  
> [!NOTE]
>  在閱讀本主題之前，您應該熟悉在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中使用頁面功能進行結構化巡覽的概念。  如需這兩個主題的詳細資訊，請參閱[結構化巡覽概觀](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)。  
  
 此主題包括下列章節：  
  
-   [巡覽拓撲](#Navigation_Topologies)  
  
-   [結構化巡覽拓撲](#Structured_Navigation_Topologies)  
  
-   [透過固定線性拓撲巡覽](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [透過固定的階層式拓撲動態巡覽](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [透過動態產生的拓撲巡覽](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## 巡覽拓撲  
 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中，巡覽拓撲一般是由含有超連結 \(<xref:System.Windows.Documents.Hyperlink>\) 的頁面 \(<xref:System.Windows.Controls.Page>\) 組成，按下超連結即會巡覽至其他頁面。  巡覽至哪個頁面則由[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] \(請參閱 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)\) 識別。  以下這個簡單的範例會顯示頁面、超連結和[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]：  
  
 [!code-xml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 這些頁面是排列在「*巡覽拓撲*」\(Navigation Topology\) 中，該拓撲的結構是由您可以在頁面之間巡覽的方式決定。  這個特定的巡覽拓撲適合用在簡單的案例，但是巡覽可能需要更複雜的拓撲，其中有些只能在應用程式執行時定義。  
  
 本主題涵蓋三種常見的巡覽拓撲：「*固定線性*」\(Fixed Linear\)、「*固定的階層式*」\(Fixed Hierarchical\) 和「*動態產生*」\(Dynamically Generated\)。  每種巡覽拓撲都用一個範例來說明，這些範例都有如下圖所示的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]：  
  
 ![具有資料項目的工作頁面](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")  
  
<a name="Structured_Navigation_Topologies"></a>   
## 結構化巡覽拓撲  
 巡覽拓撲可分為兩大類：  
  
-   **固定拓撲**：於編譯時期定義，在執行階段不會改變。  以線性或階層架構順序巡覽一連串固定順序的頁面時，固定拓撲十分有用。  
  
-   **動態拓撲**：根據從使用者、應用程式或系統收集的輸入於執行階段定義。  當可能以不同順利巡覽頁面時，動態拓撲十分有用。  
  
 雖然可以用頁面建立巡覽拓撲，但範例中仍會使用頁面功能，因為頁面功能提供的額外支援可以簡化透過拓撲的頁面進行資料傳遞和傳回的程序。  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## 透過固定線性拓撲巡覽  
 請想像有個精靈具有一個或多個要以固定順序巡覽的精靈頁面，固定線性拓撲就類似這個精靈的結構。  下圖顯示固定線性拓撲精靈的大致結構和流程。  
  
 ![巡覽拓撲圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")  
  
 透過固定線性拓撲巡覽的一般行為有：  
  
-   從呼叫頁面巡覽至啟動程式頁面，該啟動程式頁面會初始化精靈，並巡覽至第一個精靈頁面。  因為呼叫頁面可以直接呼叫第一個精靈頁面，所以啟動程式頁面 \(無 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 <xref:System.Windows.Navigation.PageFunction%601>\) 並不是必要的。  但是，如果精靈的初始化作業相當複雜，使用呼叫頁面可以簡化初始化作業。  
  
-   使用者可以透過 \[上一頁\] 和 \[下一頁\] 按鈕 \(或超連結\) 來巡覽頁面。  
  
-   使用者可以使用日誌來巡覽頁面。  
  
-   使用者可以在精靈的任一頁按下 \[取消\] 按鈕來取消精靈。  
  
-   使用者可以在精靈的最後一頁按下 \[完成\] 按鈕來接受精靈。  
  
-   如果取消精靈，該精靈將傳回適當的結果，而且不會傳回任何資料。  
  
-   如果使用者接受精靈，該精靈將傳回適當的結果和它收集的資料。  
  
-   精靈完成 \(接受或取消\) 時，精靈所包含的頁面便會從日誌中移除。  這可以確保精靈的每個執行個體都受到隔離，因而避免資料或狀態異常的可能性。  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## 透過固定的階層式拓撲動態巡覽  
 在某些應用程式中，可以從一個頁面巡覽至兩個以上的其他頁面，如下圖所示。  
  
 ![可巡覽至多個頁面的頁面](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")  
  
 這種結構稱為「固定的階層式拓撲」，在階層中的周遊順序通常是在執行階段由應用程式或使用者決定。  階層中每個可以巡覽至兩個以上其他頁面的頁面，都會在執行階段收集所需的資料以決定要巡覽至哪個頁面。  下圖根據之前的圖，顯示數個可能的巡覽順序的其中之一。  
  
 ![巡覽拓撲圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")  
  
 儘管在固定的階層式結構中頁面的巡覽順序是在執行階段決定，使用者的經驗和固定線性拓撲的使用者一樣：  
  
-   從呼叫頁面巡覽至啟動程式頁面，該啟動程式頁面會初始化精靈，並巡覽至第一個精靈頁面。  因為呼叫頁面可以直接呼叫第一個精靈頁面，所以啟動程式頁面 \(無 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 <xref:System.Windows.Navigation.PageFunction%601>\) 並不是必要的。  但是，如果精靈的初始化作業相當複雜，使用呼叫頁面可以簡化初始化作業。  
  
-   使用者可以透過 \[上一頁\] 和 \[下一頁\] 按鈕 \(或超連結\) 來巡覽頁面。  
  
-   使用者可以使用日誌來巡覽頁面。  
  
-   使用者如果在日誌中向後巡覽，可以變更巡覽順序。  
  
-   使用者可以在精靈的任一頁按下 \[取消\] 按鈕來取消精靈。  
  
-   使用者可以在精靈的最後一頁按下 \[完成\] 按鈕來接受精靈。  
  
-   如果取消精靈，該精靈將傳回適當的結果，而且不會傳回任何資料。  
  
-   如果使用者接受精靈，該精靈將傳回適當的結果和它收集的資料。  
  
-   精靈完成 \(接受或取消\) 時，精靈所包含的頁面便會從日誌中移除。  這可以確保精靈的每個執行個體都受到隔離，因而避免資料或狀態異常的可能性。  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## 透過動態產生的拓撲巡覽  
 在某些應用程式中，兩個以上頁面的巡覽順序只能在執行階段由使用者、應用程式或外部資料決定。  下圖說明尚未決定巡覽順序的一組頁面。  
  
 ![巡覽拓撲圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")  
  
 接下來這張圖說明使用者在執行階段選擇的巡覽順序。  
  
 ![巡覽圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")  
  
 這個巡覽順序稱為「動態產生的拓撲」。  對使用者來說，和其他巡覽拓撲的使用者相比較，使用者的經驗和使用前述拓撲的使用者一樣：  
  
-   從呼叫頁面巡覽至啟動程式頁面，該啟動程式頁面會初始化精靈，並巡覽至第一個精靈頁面。  因為呼叫頁面可以直接呼叫第一個精靈頁面，所以啟動程式頁面 \(無 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 <xref:System.Windows.Navigation.PageFunction%601>\) 並不是必要的。  但是，如果精靈的初始化作業相當複雜，使用呼叫頁面可以簡化初始化作業。  
  
-   使用者可以透過 \[上一頁\] 和 \[下一頁\] 按鈕 \(或超連結\) 來巡覽頁面。  
  
-   使用者可以使用日誌來巡覽頁面。  
  
-   使用者可以在精靈的任一頁按下 \[取消\] 按鈕來取消精靈。  
  
-   使用者可以在精靈的最後一頁按下 \[完成\] 按鈕來接受精靈。  
  
-   如果取消精靈，該精靈將傳回適當的結果，而且不會傳回任何資料。  
  
-   如果使用者接受精靈，該精靈將傳回適當的結果和它收集的資料。  
  
-   精靈完成 \(接受或取消\) 時，精靈所包含的頁面便會從日誌中移除。  這可以確保精靈的每個執行個體都受到隔離，因而避免資料或狀態異常的可能性。  
  
## 請參閱  
 <xref:System.Windows.Controls.Page>   
 <xref:System.Windows.Navigation.PageFunction%601>   
 <xref:System.Windows.Navigation.NavigationService>   
 [結構化巡覽概觀](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)