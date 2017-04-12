---
title: "DataRepeater 控制項 (Visual Studio) 中的虛擬模式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- virtual data binding
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 85f7e250c57a507e891eb30756c0550098cce9e0
ms.lasthandoff: 03/13/2017

---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater 控制項中的虛擬模式 (Visual Studio)
當您想要顯示表格式資料中的大量<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，您可以改善效能，藉由設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性`True`和明確地管理其資料來源控制項的互動。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項提供數個與您的資料來源進行互動，並視需要在執行階段顯示的資料，您可以處理的事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="how-virtual-mode-works"></a>虛擬模式運作  
 最常見的案例<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是繫結的子控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>至資料來源在設計階段，並允許<xref:System.Windows.Forms.BindingSource>傳遞資料來回視。</xref:System.Windows.Forms.BindingSource> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 當您使用的虛擬模式時，控制項未繫結至資料來源，以及資料來回傳遞至基礎資料來源在執行階段。  
  
 當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性設定為`True`，您新增的控制項建立使用者介面**工具箱**而不是加入繫結的控制項，從**資料來源**視窗。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
 針對控制項的控制項，會引發事件，而且您必須加入程式碼來處理資料的顯示。 當新<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>捲動到檢視，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>就會引發一次，每個控制項的事件，所以您必須提供每個控制項中的值<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>事件處理常式。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>  
  
 如果使用者變更其中一個控制項中的資料<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>就會引發事件，而您必須驗證資料並將它儲存到您的資料來源。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
  
 如果使用者加入新項目，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>就會引發事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> 若要建立新的記錄資料來源中使用這個事件處理常式。 若要避免非預期的變更，您也必須監視<xref:System.Windows.Forms.Control.KeyDown>事件針對每個控制項和呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>如果使用者按下 ESC 鍵。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> </xref:System.Windows.Forms.Control.KeyDown>  
  
 如果您的資料來源變更時，您可以重新整理<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，藉由呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>方法。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 這兩種方法必須呼叫順序。  
  
 最後，您必須實作的事件處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>事件，就會發生刪除項目時，也可以針對<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>每當使用者按下 DELETE 鍵刪除的項目就會發生的事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>  
  
## <a name="implementing-virtual-mode"></a>實作虛擬模式  
 以下是實作虛擬模式所需的步驟。  
  
#### <a name="to-implement-virtual-mode"></a>若要實作虛擬模式  
  
1.  拖放到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性`True`。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
2.  將控制項從**工具箱**拖曳的項目範本區域 （左上區域） 至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 您想要顯示的資料來源中每個欄位必須有一個控制項。  
  
3.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>事件以提供每個控制項的值。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> 當新時，會引發這個事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>捲動到檢視。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&#1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>來儲存資料的事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> 當使用者將變更認可至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>的子控制項時，會引發這個事件 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&#2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  實作的每個子控制項的處理常式<xref:System.Windows.Forms.Control.KeyDown>事件和監視器 ESC 鍵。</xref:System.Windows.Forms.Control.KeyDown> 呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>方法，以防止<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>引發的事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> 程式碼將類似下列的範例。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&#3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> 當使用者加入新項目，會引發這個事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&#4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>事件。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> 當使用者刪除現有的項目，就會發生此事件。 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&#5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  控制層級驗證，您可以選擇實作的處理常式<xref:System.Windows.Forms.Control.Validating>子控制項的事件。</xref:System.Windows.Forms.Control.Validating> 程式碼將類似下列的範例。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&#6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
