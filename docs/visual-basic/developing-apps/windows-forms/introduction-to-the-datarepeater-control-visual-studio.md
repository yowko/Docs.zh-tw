---
title: "Introduction to the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "repeating data"
  - "DataRepeater, overview"
  - "DataRepeater"
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Introduction to the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Basic Power Packs 中的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項是一種可捲動容器，適合顯示重複資料 \(如資料庫資料表中的資料列\) 的控制項使用。  當您需要進一步控制資料的配置時，可以使用它來替代 <xref:System.Windows.Forms.DataGridView> 控制項。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 藉由在捲動檢視中建立多個執行個體，「重複」一組相關的控制項，  這樣有助於使用者同時檢視多個資料錄。  
  
## 概觀  
 在設計階段，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項由兩個區段組成。  外部區段為「*檢視區*」\(Viewport\)，是捲動資料在執行階段的顯示位置。  內部 \(上方\) 區段稱為「*項目樣板*」\(Item Template\)，只要是置入這個位置的控制項，都會在執行階段重複出現，通常一個控制項會對應一個資料來源欄位。  項目樣板中的屬性和控制項會封裝在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 屬性中。  
  
 在執行階段，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 會被複製到虛擬 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 物件，並使用這個物件在每一筆被捲動到檢視處的資料錄中顯示資料。  您可以在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件中自訂個別資料錄的顯示，例如依照欄位值反白顯示欄位。  如需詳細資訊，請參閱 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項最常見的用途就是顯示資料庫資料表或其他繫結資料來源的資料。  除了 [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] 資料物件之外，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項還可以繫結到任何實作 <xref:System.Collections.IList> 介面 \(包括陣列\) 的類別 \(Class\)、任何實作 <xref:System.ComponentModel.IListSource> 介面的類別、任何實作 <xref:System.ComponentModel.IBindingList> 介面的類別或任何實作 <xref:System.ComponentModel.IBindingListView> 介面的類別。  
  
### 資料繫結  
 完成資料繫結的一般做法是將欄位從 \[**資料來源**\] 視窗拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項上。  如需詳細資訊，請參閱 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
 在處理大量資料時，您可以將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 屬性設定為 `True`，以顯示可用的資料子集。  虛擬模式會要求實作填入 \(Populate\) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 的資料快取，而您必須在執行階段控制所有與資料快取的互動。  如需詳細資訊，請參閱 [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。  
  
 您也可以在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項上顯示未繫結控制項，  例如顯示重複出現在每個項目上的影像。  如需詳細資訊，請參閱 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。  
  
### 事件  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項最重要的事件是 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件 \(會在新的項目被捲動到檢視處時引發\) 以及 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> 事件 \(會在項目被選取時引發\)。  您可以使用 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件變更項目的外觀，  例如將負值反白顯示。  當項目被選取時，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> 事件可以用來存取控制項的值。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項會在程式碼編輯器中公開 \(Expose\) 所有的標準控制項事件，  不過，不應該使用某些事件。  鍵盤和滑鼠事件如 `KeyDown`、`Click`、`MouseDown` 等在執行階段並不會被引發，因為 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項本身永遠不會獲得焦點 \(Focus\)。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 並不會在設計階段公開事件，因為它只有在執行階段才會產生。  如果要處理鍵盤和滑鼠事件，您可以在設計階段將 <xref:System.Windows.Forms.Panel> 控制項加入至 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>，然後處理 <xref:System.Windows.Forms.Panel> 的事件。  如需詳細資訊，請參閱 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)。  
  
### 自訂  
 在執行階段以及設計階段中，有許多種方式可以自訂 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的外觀和行為。  您可以將屬性設定為變更色彩、隱藏或修改項目標題、將方向從縱向變成橫向等等。  如需詳細資訊，請參閱 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)、[How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) 和 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)。  
  
 請注意，有些屬性適用於 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項本身，而有些屬性卻僅適用於 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>，  因此，在設定屬性前，請務必確定選取了正確的控制項區段。  如需詳細資訊，請參閱 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 其他自訂包括控制加入或刪除資料錄功能、加入搜尋功能，以及以主從式格式顯示相關資料。  如需詳細資訊，請參閱 [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)、[How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) 和 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)。  
  
## 請參閱  
 [DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [逐步解說：在 DataRepeater 控制項中顯示資料](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)