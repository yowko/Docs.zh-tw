---
title: 如何：在 DataRepeater 控制項中顯示項目標題 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: 07f6a7e06c5b1e91597ab6b6d816407a2c172278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592129"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>如何：在 DataRepeater 控制項中顯示項目標題 (Visual Studio)
中的項目標頭<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項提供視覺指標，當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>已選取。 當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設定為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>（預設值），顯示項目標題左邊的每個項目。 當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設定為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>，項目標頭會顯示在每個項目的頂端。  
  
 第一次選取時，項目標頭會顯示在所指定的色彩<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>屬性和白色箭號圖示會顯示。  
  
> [!NOTE]
>  如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.White%2A>，選取項目符號將不會顯示第一次選取項目。  
  
 中的欄位<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>具有焦點的項目標頭變更色彩<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>背景色彩和箭號圖示隨即變更為黑色。 如果資料已經變更，鉛筆符號會顯示在項目標頭。  
  
 預設寬度 (或高度時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設定為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) 項目的標頭是 15 像素為單位。 您可以藉由設定變更寬度<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性。  
  
> [!NOTE]
>  如果<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性設為小於 11 的值，將不會顯示項目標頭中的標記符號。  
  
 您可以設定，以隱藏項目標題<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>屬性**False**。 當<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>設**False**，項目已選取的唯一指示是周圍的虛線<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。  
  
> [!NOTE]
>  您也可以藉由監視提供您自己的選取範圍指標<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>屬性<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>。  
  
### <a name="to-change-the-appearance-of-item-headers"></a>若要變更項目標題的外觀  
  
1.  在 Windows Form 設計工具中，選取下方的區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
    > [!NOTE]
    >  您必須選取控制項的較低的區域。 如果您選取的項目範本區段中，一組不同的屬性會出現在 [屬性] 視窗。  
  
2.  在 [屬性] 視窗中，使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>屬性來變更項目標題的色彩。  
  
    > [!NOTE]
    >  如果您設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>至<xref:System.Drawing.Color.White%2A>，選取項目符號將不會顯示第一次選取項目。  
  
3.  使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性來變更項目標題的寬度 （或高度）。  
  
    > [!NOTE]
    >  如果<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>屬性設為小於 11 的值，將不會顯示項目標頭中的標記符號。  
  
### <a name="to-hide-item-headers"></a>若要隱藏項目標題  
  
1.  在 Windows Form 設計工具中，選取下方的區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
    > [!NOTE]
    >  您必須選取控制項的較低的區域。 如果您選取的項目範本區段中，一組不同的屬性會出現在 [屬性] 視窗。  
  
2.  在 [屬性] 視窗中，設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>屬性**False**。  
  
     中的項目時<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>已選取，唯一的指示將周圍的虛線<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [操作說明：變更 DataRepeater 控制項的配置](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
