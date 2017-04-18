---
title: "如何：處理 ContextMenuOpening 事件 | Microsoft Docs"
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
  - "ContextMenuOpening 事件"
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：處理 ContextMenuOpening 事件
您可以在應用程式中處理 <xref:System.Windows.FrameworkElement.ContextMenuOpening> 事件，以便在顯示之前先調整現有的內容功能表，或是隱藏將在其他事件中透過將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 屬性設定為 `true` 來顯示的功能表。  在事件資料中將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true` 的原因通常是要將功能表全部取代成新的 <xref:System.Windows.Controls.ContextMenu> 物件，而這有時候必須取消作業並啟動新的開啟作業。  如果您撰寫 <xref:System.Windows.FrameworkElement.ContextMenuOpening> 事件的處理常式，應該留意 <xref:System.Windows.Controls.ContextMenu> 控制項與通常負責開啟及定位控制項內容功能表之服務間的時機問題。  本主題說明適用於各種內容功能表開啟案例的部分程式碼技巧，並舉例說明必須注意時機問題的情況。  
  
 有幾個案例必須處理 <xref:System.Windows.FrameworkElement.ContextMenuOpening> 事件：  
  
-   在顯示之前調整功能表項目。  
  
-   在顯示之前取代整個功能表。  
  
-   完全隱藏任何現有的內容功能表，而且不顯示任何內容功能表。  
  
## 範例  
  
## 在顯示之前調整功能表項目  
 調整現有的功能表項目相當簡單，而且可能是最常見的案例。  您可以執行這個動作以便增加或減少內容功能表選項，藉以反應應用程式中目前的狀態資訊，或是在要求內容功能表之物件中做為屬性使用的特定狀態資訊。  
  
 一般方法是取得事件的來源，也就是以滑鼠右鍵按一下的特定控制項，並從其中取得 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 屬性。  您通常需要檢查 <xref:System.Windows.Controls.ItemsControl.Items%2A> 集合，確定功能表中已經存在哪些內容功能表項目，然後在集合中加入或移除適當的新 <xref:System.Windows.Controls.MenuItem> 項目。  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## 在顯示之前取代整個功能表  
 另外一個案例是您想取代整個內容功能表。  您當然也可以使用前述程式碼的變化，移除現有內容功能表的每個項目，並從項目零開始加入新項目。  但是取代內容功能表中所有項目比較簡單直接的方法是建立新的 <xref:System.Windows.Controls.ContextMenu>、填入 \(Populate\) 項目，然後將控制項的 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName> 屬性設定成新的 <xref:System.Windows.Controls.ContextMenu>。  
  
 下面是用來取代 <xref:System.Windows.Controls.ContextMenu> 的簡單處理常式程式碼。  此程式碼參考自訂 `BuildMenu` 方法，將此方法區隔開的原因是呼叫它的範例處理常式超過一個。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 不過，將這種處理常式樣式用於 <xref:System.Windows.FrameworkElement.ContextMenuOpening>，如果您在其中設定 <xref:System.Windows.Controls.ContextMenu> 的物件沒有已經存在的內容功能表，可能會暴露出時機的問題。  當使用者以滑鼠右鍵按一下控制項時，即使現有的 <xref:System.Windows.Controls.ContextMenu> 是空白或 null，還是會引發 <xref:System.Windows.FrameworkElement.ContextMenuOpening>。  但是在這種情況下，您在來源項目上設定的任何新 <xref:System.Windows.Controls.ContextMenu> 都會因為送達的時間太晚而無法顯示。  此外，如果使用者正好又按了一次滑鼠右鍵，這一次當處理常式再次執行時，您的新 <xref:System.Windows.Controls.ContextMenu> 就會出現，值不是 null，而且處理常式也會正確取代及顯示功能表。  這代表可能的解決辦法有兩種：  
  
1.  確定 <xref:System.Windows.FrameworkElement.ContextMenuOpening> 處理常式執行對象一律為至少提供一個替代符號 \(Placeholder\) <xref:System.Windows.Controls.ContextMenu> 的控制項，而您想要將該替代符號取代為處理常式程式碼。  在這種情況下，您還是可以使用上述範例中顯示的處理常式，但是您通常需要在初始標記中指派替代符號 <xref:System.Windows.Controls.ContextMenu>。  
  
     [!code-xml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  假設根據某種初步邏輯，初始 <xref:System.Windows.Controls.ContextMenu> 值可能為 null，  您可以檢查 <xref:System.Windows.Controls.ContextMenu> 是否為 null，或是使用程式碼中的旗標檢查處理常式是否已經執行至少一次以上。  由於您認為 <xref:System.Windows.Controls.ContextMenu> 即將顯示，因此處理常式接著會在事件資料中將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true`。  對於負責顯示內容功能表的 <xref:System.Windows.Controls.ContextMenuService> 而言，事件資料中 <xref:System.Windows.RoutedEventArgs.Handled%2A> 的 `true` 值代表要求取消顯示引發此事件的內容功能表\/控制項組合。  
  
 現在，您已隱藏了可能有問題的內容功能表，下一個步驟是提供新的功能表，然後再顯示它。  設定新功能表基本上與前面的處理常式相同：您會建置新的 <xref:System.Windows.Controls.ContextMenu>，然後再用它設定控制項來源的 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName> 屬性。  增加的步驟是您現在必須強制顯示內容功能表，因為您已抑制了第一次的嘗試。  若要強制顯示，請於處理常式內將 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=fullName> 屬性設定為 `true`。  執行這個步驟時請特別小心，因為在處理常式中開啟內容功能表會再次引發 <xref:System.Windows.FrameworkElement.ContextMenuOpening> 事件。  若您重新進入處理常式，它就會變成無限遞迴。  因此，如果您是從 <xref:System.Windows.FrameworkElement.ContextMenuOpening> 事件處理常式 \(Event Handler\) 開啟內容功能表，請務必檢查 `null` 或使用旗標。  
  
## 隱藏任何現有的內容功能表而且不顯示任何內容功能表  
 最後的案例，也就是撰寫完全隱藏功能表的處理常式，並不常見。  如果指定的控制項不應該顯示內容功能表，除了只在使用者要求時隱藏功能表以外，可能還有更適當的方法可以確保這一點。  但是如果您想使用處理常式隱藏內容功能表而且不想顯示任何項目，則處理常式應該直接在事件資料中將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true`。  負責顯示內容功能表的 <xref:System.Windows.Controls.ContextMenuService> 將會檢查它在控制項上引發之事件的事件資料。  如果該事件在路由中任何地方標記為 <xref:System.Windows.RoutedEventArgs.Handled%2A>，便會隱藏啟始事件的內容功能表開啟動作。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ContextMenu>   
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName>   
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [ContextMenu 概觀](../../../../docs/framework/wpf/controls/contextmenu-overview.md)