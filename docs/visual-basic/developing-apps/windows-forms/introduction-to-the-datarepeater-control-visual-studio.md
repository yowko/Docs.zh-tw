---
title: "介紹 DataRepeater 控制項 (Visual Studio) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86078426494caabefc6bbfb036037007e830e1cb
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater 控制項簡介 (Visual Studio)
Visual Basic Power Pack<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是可捲動的容器控制項，顯示重複的資料，例如，資料列中的資料庫資料表。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 作為替代<xref:System.Windows.Forms.DataGridView>控制當您需要更充分掌控的資料配置。</xref:System.Windows.Forms.DataGridView> <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>在捲動檢視中建立多個執行個體的 「 重複 」 相關的控制項群組。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 這可讓使用者同時檢視多個資料錄。  
  
## <a name="overview"></a>概觀  
 在設計階段，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項包含兩個區段。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> [外部] 區段*檢視區*，會在執行階段顯示捲動的資料。 內部 （上方） 區段，稱為*項目範本*，這個位置就會重複出現在執行階段，通常一個控制項的資料來源中每個欄位的控制項。 屬性和項目範本中的控制項，都會封裝在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>屬性。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>  
  
 在執行階段，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>會複製到虛擬<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>物件，用來顯示資料，當每個資料錄捲動到檢視。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 您可以自訂顯示在個別記錄<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件，例如，反白顯示的欄位，根據它所包含的值。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 如需詳細資訊，請參閱[How to︰ 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 最常見的用法<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是以顯示來自資料庫資料表或其他繫結的資料來源的資料。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 除了[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]資料物件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可以繫結至任何實作類別<xref:System.Collections.IList>（包括陣列） 的介面，任何實作類別<xref:System.ComponentModel.IListSource>介面，任何實作類別<xref:System.ComponentModel.IBindingList>介面或任何實作類別<xref:System.ComponentModel.IBindingListView>介面。</xref:System.ComponentModel.IBindingListView> </xref:System.ComponentModel.IBindingList> </xref:System.ComponentModel.IListSource> </xref:System.Collections.IList> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
### <a name="data-binding"></a>資料繫結  
 一般而言，您完成資料繫結中的欄位拖曳**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 如需詳細資訊，請參閱[How to︰ 在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
 當使用大量的資料，您可以設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性`True`以顯示可用的資料子集。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 虛擬模式需要的資料快取的實作<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>已填入，而且您必須在執行階段控制的資料快取的所有互動。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 如需詳細資訊，請參閱[DataRepeater 控制項中的虛擬模式](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。  
  
 您也可以顯示未繫結的控制項上<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 比方說，您可以在每個項目上顯示重複的映像。 如需詳細資訊，請參閱[How to︰ 在 DataRepeater 控制項中顯示未繫結控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。  
  
### <a name="events"></a>事件  
 最重要的事件，如<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制是<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件引發時，新的項目會捲動到檢視時，和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>事件會在選取的項目時引發。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 您可以使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件來變更之項目的外觀。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 例如，您可以反白顯示負數值。 使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>事件來選取項目時，存取控制項的值。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項也會公開所有的一般控制項事件在程式碼編輯器。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 不過，某些事件不應。 鍵盤和滑鼠事件，例如`KeyDown`， `Click`，和`MouseDown`將不會引發執行階段因為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身永遠不會有焦點。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>不會公開事件在設計階段建立只能在執行階段因為。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 如果您想要處理鍵盤和滑鼠事件，您可以加入<xref:System.Windows.Forms.Panel>，來控制對<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>在設計階段，然後處理的事件<xref:System.Windows.Forms.Panel>.</xref:System.Windows.Forms.Panel> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:System.Windows.Forms.Panel> 如需詳細資訊，請參閱[疑難排解 DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)。  
  
### <a name="customizations"></a>自訂  
 有許多方法可以自訂外觀和行為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制，請在執行階段和設計階段。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 若要變更色彩、 隱藏或修改項目標題、 變更方向，從以水平、 垂直等等，可以設定屬性。 如需詳細資訊，請參閱[How to︰ 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)， [How to: DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)，和[How to︰ 變更 DataRepeater 控制項的配置](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)。  
  
 請注意，某些屬性會套用到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身，而有些則只會套用到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 請確定您有正確的區段，選取之前設定屬性的控制項。 如需詳細資訊，請參閱[How to︰ 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)。  
  
 其他自訂包括控制加入或刪除記錄的能力、 加入搜尋功能，以及主要和詳細的格式顯示相關的資料。 如需詳細資訊，請參閱[How to︰ 停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)， [How to︰ 搜尋 DataRepeater 控制項中的資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)，和[如何︰ 建立主版/詳細表單所使用兩個 DataRepeater 控制項 (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [DataRepeater 控制項](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [逐步解說︰ 在 DataRepeater 控制項中顯示資料](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
