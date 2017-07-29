---
title: "Manipulations and Inertia Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Manipulations and Inertia Overview
*操作*可讓使用者使用*操作工具*來移動、旋轉和調整使用者介面 \(UI\) 項目大小。  操作工具代表滑鼠或 \(在觸控式的情況下\) 手寫筆或手指。  
  
 *慣性*藉由在項目上模擬摩擦力，可模擬移動的 UI 項目在真實世界中的行為。  這可讓項目在停止前逐漸減緩移動 \(直線和有角度的方向\)。  本文提供 .NET Framework 操作和慣性的簡介。  
  
## 操作  
 操作視操作工具的集合為複合物件。  應用程式可以追蹤複合物件的變更，而非個別元件的變更。  
  
 請考慮下圖中的影像。  使用者可以使用兩個操作工具來移動、旋轉和縮放影像。  對每個操作工具的變更會與其他操作工具一同被解譯。  
  
 例如，如果您在影像上有兩個操作工具 \(1 和 2\)，且您以 \+Y 方向 \(下\) 移動操作工具 1，則該影像的變更會取決於操作工具 2 產生的變化。  如果操作工具 2 也以 \+Y \(下\) 的方向移動，則該影像就會直接以 \+Y 方向移動。  但若操作工具 2 沒有變更，或以 \-Y 方向 \(上\) 移動，則該影像會變小或旋轉。  
  
 ![兩隻指頭正在操作的虛擬相片。](../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation\_Resize")  
  
 受兩個操作工具所管理的影像  
  
 操作處理可提供監視操作工具子集的架構，並會解譯它們，如同一起動作，而非獨立地動作。  您可以同時建立數個操作處理器物件，可在應用程式中操作每個 UI 項目。  會通知操作處理器要觀察哪個輸入裝置，並透過 [.NET 事件](http://msdn.microsoft.com/library/17sde2xt.aspx)報告操作。  
  
 操作處理器沒有受管理之特定項目的資訊。  應用程式會各自將變更套用至特定應用程式項目。  例如，應用程式將轉換套用至影像或重新繪製，在新的位置以新的大小或方向顯示。  
  
 為二維 \(2D\) [仿射轉換](http://msdn.microsoft.com/library/ms533810\(VS.85\).aspx)所設計的操作。  這些轉換包含平移、旋轉和縮放。  
  
### 操作的各部分  
 操作是 <xref:System.Windows.Input.Manipulations.Manipulator2D> 物件的集合。  此彙總的操作會由原點和橢圓形呈現。  原點是操控項目的所有操作工具的平均位置。  此橢圓形的半徑為從原點到每個 <xref:System.Windows.Input.Manipulations.Manipulator2D> 物件的平均距離。  
  
 ![操作的各部分。](../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation\_Definition")  
  
 兩個操作工具 \(1 和 2\)、一個原點和一個橢圓形可指定一項操作  
  
 加入、移動或移除 UI 項目的操作工具時，應用程式會呼叫 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> 方法來更新 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> 物件。  操作第一次開始時，會引發 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> 事件。  
  
> [!NOTE]
>  在以框架為基礎的更新環境中使用時，操作處理會更有效率。  當在 Microsoft XNA 應用程式中使用操作處理時，這不成問題，因為 XNA Framework 會使用 [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法來提供以框架為基礎的更新。  在另一個環境中 \(例如 WinForms\)，您可能會需要提供您自己以框架為基礎的邏輯，以收集操作，並定期以批次方式傳送到 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A>。  
  
 當操作工具或其位置的數目變更時，會引發 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> 事件。  傳遞至 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> 事件處理常式的 <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> 物件屬性會指定最後一個事件發生後原點、縮放、旋轉和轉譯的變更。  當操作工具移動時，以及當新增或移除操作工具時，就會變更操作的原點。  轉譯值指定此操作包含多少 X 或 Y 移動。  
  
 應用程式使用新的值來重新繪製 UI 項目。  
  
 ![接觸點 A 移動到右邊後的操作。](../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation\_Changed")  
  
 操作工具 1 移動，並造成原點變更  
  
 從 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> 物件中移除最後一個與操作相關聯的操作工具時，會引發 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> 事件。  
  
### 操作處理模型  
 操作處理器會使用直接使用方式模型。  藉由這個簡單的模型，應用程式必須將任何輸入事件的詳細資料傳遞給操作處理器。  輸入的事件可能會由任何基本輸入所引發，例如滑鼠裝置、手寫筆或手指。  這個程序提供直接的篩選機制以及簡單的使用模型，讓應用程式在必要時可以批次輸入事件。  
  
 對於要在操作程序中包含基本輸入的應用程式，它會從基本輸入的詳細資料建立 <xref:System.Windows.Input.Manipulations.Manipulator2D> 結構，並使用 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> 方法將結構傳遞給操作處理器。  操作處理器接著會引發事件，其中應用程式必須適當地處理視覺化元件的更新。  
  
 ![操作直接使用方式模型的流程。](../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation\_Flow")  
  
 操作處理模型  
  
## 慣性  
 慣性處理器可讓應用程式模擬真實世界行為，來外推位置、方向與其他 UI 項目的屬性。  
  
 例如，當使用者撥動項目，它可以繼續移動、減速，並慢慢停止。  慣性處理器會實作此行為，讓仿射 2D 值 \(原點、縮放、轉譯和旋轉\) 在指定時間內以指定減速速率變更。  
  
 如同操作處理，慣性處理器並沒有任何特定 UI 項目的相關資訊。  為了回應 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> 物件引發的事件，應用程式會分別將變更套用至應用程式特定的項目。  
  
 慣性處理和操作處理通常一起使用。  其介面很類似，而且它們所引發的事件 \(在某些情況下\) 完全相同。  一般而言，當 UI 項目操作完成時，就會開始慣性處理。  這透過接聽 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> 事件和從事件處理常式啟動慣性處理而完成。  
  
## 請參閱  
 <xref:System.Windows.Input.Manipulations>