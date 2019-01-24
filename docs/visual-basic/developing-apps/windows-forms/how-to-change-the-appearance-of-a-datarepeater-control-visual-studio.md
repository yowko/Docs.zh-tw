---
title: HOW TO：變更 DataRepeater 控制項 (Visual Studio) 的外觀
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716631"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>HOW TO：變更 DataRepeater 控制項 (Visual Studio) 的外觀
您可以變更的外觀<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在設計階段設定屬性，或在執行階段處理<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件。  
  
 您在選取之控制項的項目範本 區段時的設計階段設定的屬性會針對每個重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>在執行階段。 外觀相關屬性<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項本身會顯示在執行階段容器的組件才會保留未涵蓋範圍 (例如，如果<xref:System.Windows.Forms.Control.Padding%2A>屬性設定為較大的值)。  
  
 在執行階段，外觀相關屬性可以是根據設定的條件。 比方說，在排程的應用程式中，您可能會變更項目的背景色彩逾期未付帳款的項目時，警告使用者。 在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，如果您設定屬性條件陳述式，例如`If…Then`，您也必須使用`Else`子句來指定不符合條件時的外觀。  
  
### <a name="to-change-the-appearance-at-design-time"></a>若要變更在設計階段外觀  
  
1.  在 Windows Form 設計工具中，選取 項目範本 （上方） 區域的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
2.  在 [屬性] 視窗中，選取屬性，並將值變更。 會影響外觀的通用屬性包括<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>， <xref:System.Windows.Forms.Panel.BorderStyle%2A>，和<xref:System.Windows.Forms.Control.ForeColor%2A>。  
  
### <a name="to-change-the-appearance-at-run-time"></a>若要變更在執行階段外觀  
  
1.  在 [程式碼編輯器] 中，按一下 [事件] 下拉式清單中的 [DrawItem] 。  
  
2.  在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，加入程式碼來設定屬性：  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>範例  
 針對一些常見的自訂<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項包含替代色彩和變更色彩的欄位，根據條件中顯示的資料列。 下列範例示範如何執行這些自訂項目。 這個範例假設您有<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>繫結至 Northwind 資料庫中的 [產品] 資料表的控制項。  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 請注意，這兩個自訂項目，您必須提供程式碼來設定條件的兩方的屬性。 如果您未指定`Else`條件，您會在執行階段看到非預期的結果。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示未繫結的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
