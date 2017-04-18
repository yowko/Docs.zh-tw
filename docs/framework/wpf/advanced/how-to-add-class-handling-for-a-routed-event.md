---
title: "如何：加入路由事件的類別處理 | Microsoft Docs"
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
  - "類別處理常式, 路由事件"
  - "路由事件, 類別處理常式"
  - "task_core_add_class_handling_routed_event"
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：加入路由事件的類別處理
路由事件可在路由中的任何指定節點上由類別處理常式或執行個體處理常式進行處理。  類別處理常式會先叫用，而且類別實作可用它來防止事件進行執行個體處理，或在基底類別擁有的事件上引入其他事件特定行為。  本範例將說明兩種密切相關的類別處理常式實作技術。  
  
## 範例  
 這個範例會使用以 <xref:System.Windows.Controls.Canvas> 面板為基礎的自訂類別。  應用程式的基本前提是，自訂類別會在子項目類別或其上的任何執行個體處理常式叫用之前，先在其子項目上引入行為，包括攔截任何滑鼠左鍵按選事件並標示為已處理。  
  
 <xref:System.Windows.UIElement> 類別會公開虛擬方法，只要覆寫事件就能在 <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> 事件上啟用類別處理。  如果類別的階層架構有此虛擬方法，這就是實作類別處理最簡單的方式。  下列程式碼顯示衍生自 <xref:System.Windows.Controls.Canvas> 的 "MyEditContainer" 中的 <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> 實作。  此實作會在引數中將事件標示為已處理，然後加入一些程式碼，以提供來源項目基本的可見變更。  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 如果基底類別上沒有虛擬方法，或該特定方法並非虛擬，類別處理可直接使用 <xref:System.Windows.EventManager> 類別的公用程式方法 <xref:System.Windows.EventManager.RegisterClassHandler%2A> 加入。  此方法只能從加入類別處理之類別的靜態初始設定中呼叫。  這個範例會加入 <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> 的另一個處理常式，這次的註冊類別是自訂類別。  相反地，當使用虛擬方法時，註冊類別其實是 <xref:System.Windows.UIElement> 基底類別。  在基底類別和子類別個別註冊類別處理的情況下，子類別處理常式會先叫用。  在應用程式中的行為就是，首先這個處理常式會顯示其訊息方塊，然後再顯示虛擬方法的處理常式中的可見變更。  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## 請參閱  
 <xref:System.Windows.EventManager>   
 [將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [處理路由事件](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)