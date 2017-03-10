---
title: "Virtual Mode in the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "virtual data binding"
  - "DataRepeater"
  - "DataRepeater, virtual mode"
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Virtual Mode in the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當您想要在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中顯示大量的表格式資料時，只要將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 屬性設定為 `True` 並明確管理控制項與其資料來源的互動，就可以改善效能。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項提供幾個事件，您可以處理這些事件以便與資料來源互動，並視需要於執行階段顯示資料。  
  
## 虛擬模式的運作方式  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項最常見的案例是在設計階段將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 的子控制項繫結到資料來源，並且視需要允許 <xref:System.Windows.Forms.BindingSource> 來回傳遞資料。  使用虛擬模式時，控制項並不會繫結到資料來源，而且資料在執行階段會來回傳遞到基礎資料來源。  
  
 在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 屬性設定為 `True` 的情況下，建立使用者介面的方式是從 \[**工具箱**\] 加入控制項，而不是從 \[**資料來源**\] 視窗加入繫結控制項。  
  
 事件引發時是以一個控制項接著一個控制項的方式，所以您必須加入程式碼來處理資料的顯示。  當新的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 被捲動到檢視處時，會為每個控制項引發 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> 事件一次，因此您必須在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> 事件處理常式中為每個控制項提供值。  
  
 如果使用者變更其中一個控制項內的資料，會引發 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> 事件，因此您必須驗證資料並將資料儲存到資料來源。  
  
 如果使用者加入新的項目，會引發 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> 事件。  請使用這個事件的處理常式，以在資料來源中建立新的資料錄。  為了防止非預期的變更，您必須監視每個控制項的 <xref:System.Windows.Forms.Control.KeyDown> 事件，以及在使用者按 ESC 鍵的情況下，呼叫 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>。  
  
 如果您的資料來源發生變更，可以藉由呼叫 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetTemplateItem%2A> 和 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetTemplateItem%2A> 方法重新整理 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。  這兩種方法都必須依照順序呼叫。  
  
 最後，您必須實作 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> 事件 \(刪除項目時發生\) 的事件處理常式，並選擇性地實作 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> 和 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> 事件 \(使用者按 DELETE 鍵刪除項目時發生\) 的事件處理常式。  
  
## 實作虛擬模式  
 以下是實作虛擬模式所需的步驟。  
  
#### 若要實作虛擬模式  
  
1.  將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項從 \[**工具箱**\] 裡的 \[**Visual Basic PowerPacks**\] 索引標籤拖曳至表單或容器控制項。  並將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 屬性設定為 `True`。  
  
2.  從 \[**工具箱**\] 中將控制項拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目樣板區域 \(上方區域\) 上。  每一個要顯示的資料來源欄位都需要一個控制項。  
  
3.  實作 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> 事件的處理常式，以提供值給每個控制項。  當新的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 被捲動到檢視處時，就會引發這個事件。  此處所述的程式碼與下列 `Employees` 資料來源使用的範例類似。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#1)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#1)]  
  
4.  實作 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> 事件的處理常式，以儲存資料。  當使用者把變更認可到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 的子控制項時，就會引發這個事件。  此處所述的程式碼與下列 `Employees` 資料來源使用的範例類似。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#2)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#2)]  
  
5.  實作每個子控制項的 <xref:System.Windows.Forms.Control.KeyDown> 事件之處理常式，並監視 ESC 鍵。  呼叫 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> 方法，以防止引發 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> 事件。  此處所述的程式碼與下列範例類似。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#3)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#3)]  
  
6.  實作 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> 事件的處理常式。  當使用者將新項目加入到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項時，就會引發這個事件。  此處所述的程式碼與下列 `Employees` 資料來源使用的範例類似。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#4)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#4)]  
  
7.  實作 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> 事件的處理常式。  當使用者刪除現有項目時，就會引發這個事件。  此處所述的程式碼與下列 `Employees` 資料來源使用的範例類似。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#5)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#5)]  
  
8.  針對控制項層級的驗證，選擇性地實作子控制項的 <xref:System.Windows.Forms.Control.Validating> 事件之處理常式。  此處所述的程式碼與下列範例類似。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksDataRepeaterVirtualMode/VbPowerPacksDataRepeaterVirtualMode.vb#6)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksDataRepeaterVirtualModeCS/VbPowerPacksDataRepeaterVirtualMode.cs#6)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)