---
title: HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示未繫結的控制項
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730785"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示未繫結的控制項
除了繫結的控制項，您可能想要新增其他控制項來<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，例如靜態標籤或映像中的每個項目上重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
> [!NOTE]
>  您也必須擁有至少一個繫結的控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>或將不會顯示在執行階段。  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>未繫結的控制項加入 DataRepeater  
  
1.  拖曳<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  拖曳調整大小和位置的控點大小和控制項的位置。  
  
     您可以調整大小，並藉由變更控制項的位置**大小**並**位置**屬性 視窗中的屬性。  
  
3.  將至少一個資料繫結控制項加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。 如需詳細資訊，請參閱[＜How to：DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。  
  
4.  將控制項從**工具箱**上的項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
     請注意，此控制項有兩個矩形區域。 內部的區域*項目範本*; 將重複控制項新增至範本中的每個項目中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在執行階段。 外部的區域*viewport*，其中會顯示的項目; 會加入到此區域中的控制項將不會顯示在執行階段。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [如何：DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [如何：使用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [如何：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
