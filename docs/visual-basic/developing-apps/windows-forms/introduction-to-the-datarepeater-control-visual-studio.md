---
title: DataRepeater 控制項簡介 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591946"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater 控制項簡介 (Visual Studio)
Visual Basic Power Pack <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項是可捲動的容器，用於存放顯示重複資料的控制項，例如資料庫資料表中的資料列。 當您需要對資料的版面配置擁有更多控制權時，可以此取代 <xref:System.Windows.Forms.DataGridView> 控制項。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>藉由建立多個執行個體中的捲動檢視 「 重複 」 相關的控制項群組。 這可讓使用者同時檢視數個記錄。  
  
## <a name="overview"></a>總覽  
 在設計階段<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項包含兩個區段。 [外部] 區段是*檢視區*，會在執行階段顯示捲動的資料。 內部 （上方） 區段，稱為*項目範本*，位置會重複，在執行階段，通常一個資料來源中的每個欄位控制項的控制項。 封裝的屬性和項目範本中的控制項在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>屬性。  
  
 在執行階段，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>複製到虛擬機器<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>物件，用來顯示資料，當每個資料錄捲動到檢視。 您可以自訂此顯示器中個別記錄的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件，例如，反白顯示的欄位，根據它所包含的值。 如需詳細資訊，請參閱[如何： 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 最常用於<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是以顯示來自資料庫資料表或其他繫結的資料來源的資料。 除了[!INCLUDE[vstecado](~/includes/vstecado-md.md)]資料物件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可以繫結至任何實作類別<xref:System.Collections.IList>（包括陣列） 的介面，任何實作類別<xref:System.ComponentModel.IListSource>介面，任何實作類別<xref:System.ComponentModel.IBindingList>介面或任何實作類別<xref:System.ComponentModel.IBindingListView>介面。  
  
### <a name="data-binding"></a>資料繫結  
 一般而言，您完成資料繫結中的欄位拖曳**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱[How to： 在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
 當使用大量的資料，您可以設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性`True`顯示可用的資料子集。 虛擬模式要求實作資料快取要從中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>已填入，而且您必須在執行階段中控制資料快取的所有互動。 如需詳細資訊，請參閱[DataRepeater 控制項中的虛擬模式](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。  
  
 您也可以顯示未繫結的控制項上<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 例如，您可以在每個項目上顯示映像，並以重複。 如需詳細資訊，請參閱[How to： 在 DataRepeater 控制項中顯示未繫結控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。  
  
### <a name="events"></a>事件  
 最重要的事件，如<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制是<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件，這捲動到檢視中新項目時所引發，而<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>選取項目時引發的事件。 您可以使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件來變更之項目的外觀。 例如，您可以反白顯示負數值。 使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>事件，以選取項目時，存取控制項的值。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項不僅會公開所有的標準控制項事件的程式碼編輯器中。 不過，某些事件不應。 鍵盤和滑鼠事件，例如`KeyDown`， `Click`，和`MouseDown`將不會引發執行階段因為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身一律沒有焦點。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>不會公開事件在設計階段因為它建立只能在執行階段。 如果您想要處理鍵盤和滑鼠事件，您可以加入<xref:System.Windows.Forms.Panel>控制權傳輸至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>在設計階段，然後處理的事件<xref:System.Windows.Forms.Panel>。 如需詳細資訊，請參閱[疑難排解 DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)。  
  
### <a name="customizations"></a>自訂  
 有許多方法可自訂外觀和行為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制，請在執行階段和設計階段。 屬性可以設定來變更色彩、 隱藏或修改項目標頭、 變更方向，從垂直到水平的以及執行更多。 如需詳細資訊，請參閱[如何： 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)， [How to： 在 DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)，和[如何： 變更的版面配置DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)。  
  
 請注意，某些屬性套用至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身，而其他僅適用於<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>。 請確定您有正確的區段，選取之前設定屬性的控制項。 如需詳細資訊，請參閱[如何： 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 其他自訂項目包含控制加入或刪除記錄的能力、 加入搜尋功能，以及在主要和詳細格式中顯示相關的資料。 如需詳細資訊，請參閱[如何： 停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)，[如何： 在 DataRepeater 控制項中的搜尋資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)，和[如何： 建立，在使用兩個主要/詳細表單DataRepeater 控制項 (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [逐步解說：在 DataRepeater 控制項中顯示資料](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
