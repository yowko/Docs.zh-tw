---
title: HOW TO：DataRepeater 控制項 (Visual Studio) 中的搜尋資料
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 514e72afc9570071f57e385574456ff7d716bad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654382"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>HOW TO：DataRepeater 控制項 (Visual Studio) 中的搜尋資料
當您使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，其中包含多筆記錄，您可能想要讓的使用者搜尋特定的記錄。 而不是控制項本身中搜尋資料，您可以藉由查詢基礎實作搜尋<xref:System.Windows.Forms.BindingSource>。 如果找到的項目，您可以使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>屬性設為選取的項目，並捲動至檢視。  
  
### <a name="to-implement-search"></a>若要實作搜尋  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。  
  
2.  在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchTextBox**。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。  
  
4.  在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchButton**。 將 **Text** 屬性變更為 **Search**。  
  
5.  按兩下 <xref:System.Windows.Forms.Button> 控制項開啟 [程式碼編輯器]，然後將下列程式碼加入 `SearchButton_Click` 事件處理常式。  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     取代*ProductsBindingSource*的名稱取代<xref:System.Windows.Forms.BindingSource>如您<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，並取代*ProductID*具有您想要搜尋的欄位名稱。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [如何：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
