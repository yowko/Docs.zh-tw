---
title: DataRepeater 控制項簡介 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485712"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater 控制項簡介 (Visual Studio)
Visual Basic Power Pack <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項是可捲動的容器，用於存放顯示重複資料的控制項，例如資料庫資料表中的資料列。 當您需要對資料的版面配置擁有更多控制權時，可以此取代 <xref:System.Windows.Forms.DataGridView> 控制項。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "會重複 」 藉由建立多個執行個體在捲動檢視中的一組相關的控制項。 這可讓使用者能夠同時檢視數筆記錄。  
  
## <a name="overview"></a>總覽  
 在設計階段<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項包含兩個區段。 外部區段*viewport*，會在執行階段顯示的捲動的資料。 內部 （上方） 區段，稱為*項目範本*，這個位置會重複，在執行階段，通常一控制項的資料來源中每個欄位的控制項。 屬性和項目範本中的控制項封裝在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>屬性。  
  
 在執行階段<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>複製到虛擬<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>用來顯示資料，當每個資料錄捲動到檢視的物件。 您可以自訂個別的資料錄中的顯示<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件，比方說，反白顯示的欄位，根據它所包含的值。 如需詳細資訊，請參閱 <<c0> [ 如何： 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 最常見的用途<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是顯示從資料庫資料表或其他繫結的資料來源的資料。 除了[!INCLUDE[vstecado](~/includes/vstecado-md.md)]資料物件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可以繫結至任何實作類別<xref:System.Collections.IList>（包括陣列） 的介面，可實作任何類別<xref:System.ComponentModel.IListSource>介面，可實作任何類別<xref:System.ComponentModel.IBindingList>介面或任何實作類別<xref:System.ComponentModel.IBindingListView>介面。  
  
### <a name="data-binding"></a>資料繫結  
 一般而言，您將欄位從完成資料繫結**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱 <<c0> [ 如何： 在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
 當使用大量的資料，您可以設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性設`True`來顯示可用的資料子集。 虛擬模式要求來源的資料快取實作<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>已填入，而且您必須在執行階段控制的資料快取的所有互動。 如需詳細資訊，請參閱 < [DataRepeater 控制項中的虛擬模式](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。  
  
 您也可以顯示未繫結的控制項上<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 比方說，您也可以在每個項目上顯示重複的映像。 如需詳細資訊，請參閱 <<c0> [ 如何： 在 DataRepeater 控制項中顯示未繫結控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。  
  
### <a name="events"></a>事件  
 最重要的事件，如<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件，會引發新的項目捲動檢視時，和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>選取項目時引發的事件。 您可以使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件來變更之項目的外觀。 例如，您可以反白顯示負數值。 使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>事件來選取項目時，存取控制項的值。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項會公開所有的標準控制項事件的程式碼編輯器中。 不過，某些事件應該都不使用了。 鍵盤和滑鼠事件，例如`KeyDown`， `Click`，並`MouseDown`就不會引發在執行階段因為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身永遠不會具有焦點。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>不會公開事件在設計階段因為它會建立只有在執行階段。 如果您想要處理鍵盤和滑鼠事件，您可以新增<xref:System.Windows.Forms.Panel>若要控制<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>在設計階段，然後處理的事件<xref:System.Windows.Forms.Panel>。 如需詳細資訊，請參閱 <<c0> [ 疑難排解 DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)。  
  
### <a name="customizations"></a>自訂  
 有許多方法可以自訂外觀和行為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制，請在執行階段和設計階段。 若要變更色彩、 隱藏或修改項目的標頭、 變更方向為水平、 垂直和更多，就可以設定屬性。 如需詳細資訊，請參閱 <<c0> [ 如何： 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)，[如何： 在 DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)，和[如何： 變更版面配置DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)。  
  
 請注意，某些屬性套用至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身，而有些則只會套用到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>。 請確定您有正確的區段，選取 設定屬性的控制項。 如需詳細資訊，請參閱 <<c0> [ 如何： 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 其他自訂項目包括控制能夠新增或移除記錄、 加入搜尋功能，以及主要和詳細資料的格式顯示相關的資料。 如需詳細資訊，請參閱[如何： 停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)，[如何： 搜尋 DataRepeater 控制項中的資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)，和[How to： 建立使用兩個主版/詳細表單DataRepeater 控制項 (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [逐步解說：在 DataRepeater 控制項中顯示資料](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
