---
title: 如何：在 DataRepeater 控制項中顯示未繫結的控制項 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: 698e518a4ed10ed6cf14ccafc6833b1acf8752db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588102"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>如何：在 DataRepeater 控制項中顯示未繫結的控制項 (Visual Studio)
除了繫結控制項，您可能想要將其他控制項加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，例如靜態標籤或映像中的每個項目上的重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
> [!NOTE]
>  您也必須擁有至少一個繫結的控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>或執行任何動作將會顯示在執行階段。  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>若要將未繫結的控制項加入 DataRepeater  
  
1.  拖曳<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。  
  
2.  拖曳調整大小和位置控點大小，並置於控制項。  
  
     您可以調整大小，並藉由變更定位控制項**大小**和**位置**[屬性] 視窗中的屬性。  
  
3.  將至少一個資料繫結控制項加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱[How to： 在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
4.  將控制項從**工具箱**到的項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
     請注意控制項有兩個矩形區域。 內部的區域是*項目範本*; 將每個項目中重複加入範本中的控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在執行階段。 外部區域是*檢視區*，其中的項目會顯示; 加入到此區域的控制項將不會顯示在執行階段。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [如何： 利用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
