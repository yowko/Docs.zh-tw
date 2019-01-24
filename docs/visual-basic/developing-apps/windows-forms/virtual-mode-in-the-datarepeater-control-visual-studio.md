---
title: DataRepeater 控制項中的虛擬模式 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
ms.openlocfilehash: 3988c16746606de9f20f9a66b87539b6cea04758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700802"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater 控制項中的虛擬模式 (Visual Studio)
當您要顯示表格式資料中的大量<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，您可以改善效能，藉由設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性設`True`和明確地管理其資料來源控制項的互動。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項提供數個事件，您可以處理與您的資料來源進行互動，並視需要在執行階段顯示的資料。  
  
## <a name="how-virtual-mode-works"></a>虛擬模式的運作  
 最常見的案例<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是繫結的子控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>到資料來源在設計階段，並允許<xref:System.Windows.Forms.BindingSource>傳遞來回所需的資料。 當您使用的虛擬模式時，控制項未繫結至資料來源，以及資料來回傳遞至基礎資料來源在執行階段。  
  
 當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性設定為`True`，您新增的控制項建立使用者介面**工具箱**而非新增繫結的控制項，從**資料來源**視窗。  
  
 以控制項的控制項為基礎，會引發事件，而且您必須新增程式碼來處理資料的顯示。 當新<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>捲動到檢視中，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>就會引發一次，每個控制項的事件，而您則必須提供在每個控制項的值<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>事件處理常式。  
  
 如果其中一個控制項中的資料已由使用者<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>就會引發事件，您必須驗證資料，並將它儲存到您的資料來源。  
  
 如果使用者加入新項目，<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>就會引發事件。 若要建立新的記錄資料來源中使用這個事件處理常式。 若要避免非預期的變更，您也必須監視<xref:System.Windows.Forms.Control.KeyDown>事件的每個控制項和呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>如果使用者按下 ESC 鍵。  
  
 如果您的資料來源變更時，您可以重新整理<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，藉由呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>方法。 這兩種方法必須呼叫順序。  
  
 最後，您必須實作的事件處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>事件，以刪除項目時，以及 （選擇性），就會發生<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>每當使用者按下 DELETE 鍵刪除項目時，就會發生的事件。  
  
## <a name="implementing-virtual-mode"></a>實作虛擬模式  
 以下是實作虛擬模式所需的步驟。  
  
#### <a name="to-implement-virtual-mode"></a>若要實作虛擬模式  
  
1.  拖曳<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。 將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> 屬性設定為 `True`。  
  
2.  將控制項從**工具箱**的項目範本區域 （上方區域） 到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 您想要顯示的資料來源中每個欄位，您都需要一個控制項。  
  
3.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>事件，以提供每個控制項的值。 當新時，會引發這個事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>捲動到檢視。 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>來儲存資料的事件。 當使用者認可的子控制項的變更時，會引發這個事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  實作針對每個子控制項的處理常式<xref:System.Windows.Forms.Control.KeyDown>事件和監視器 ESC 鍵。 呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>方法，即可避免<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>引發的事件。 程式碼將類似下列的範例。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>事件。 當使用者新增至新的項目時，會引發這個事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  實作的處理常式<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>事件。 當使用者刪除現有的項目，就會發生此事件。 程式碼將類似下列的範例中，名為資料來源是`Employees`。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  為了控制層級驗證，請選擇性地實作的處理常式<xref:System.Windows.Forms.Control.Validating>子控制項的事件。 程式碼將類似下列的範例。  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>
- [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
