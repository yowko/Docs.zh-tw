---
title: 如何：搜尋 DataRepeater 控制項中的資料 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 689990ee125c85c3151a4e965b619fde068d220e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588050"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>如何：搜尋 DataRepeater 控制項中的資料 (Visual Studio)
當您使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>包含許多記錄，您可能想要讓的使用者搜尋的特定記錄的控制項。 而不是控制項本身中搜尋資料，您可以藉由查詢的基礎實作搜尋<xref:System.Windows.Forms.BindingSource>。 如果找到項目，然後您可以使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>屬性設為選取的項目，並捲動至檢視。  
  
### <a name="to-implement-search"></a>若要實作搜尋  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。  
  
2.  在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchTextBox**。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。  
  
4.  在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchButton**。 將 **Text** 屬性變更為 **Search**。  
  
5.  按兩下 <xref:System.Windows.Forms.Button> 控制項開啟 [程式碼編輯器]，然後將下列程式碼加入 `SearchButton_Click` 事件處理常式。  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     取代*ProductsBindingSource*名稱<xref:System.Windows.Forms.BindingSource>如您<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，並取代*ProductID*具有您想要搜尋的欄位名稱。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
