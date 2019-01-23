---
title: HOW TO：變更 DataRepeater 控制項 (Visual Studio) 的配置
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625597"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>HOW TO：變更 DataRepeater 控制項 (Visual Studio) 的配置
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可以顯示在 （項目捲動垂直） 的垂直或水平 （項目捲動水平） 的方向。 您可以變更方向，在設計階段或執行階段變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性。 如果您變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>在執行階段的屬性，您可能也想要調整大小<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>和重新調整子控制項位置。  
  
> [!NOTE]
>  如果您重新調整控制項位置上<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>在執行階段，您必須呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>開頭和結尾程式碼區塊，重新調整控制項位置的方法。  
  
### <a name="to-change-the-layout-at-design-time"></a>若要在設計階段變更版面配置  
  
1.  在 Windows Form 設計工具中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。  
  
    > [!NOTE]
    >  您必須選擇其外部框線<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項中下方區域的控制項，不會在右上角按一下<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>區域。  
  
2.  在 [屬性] 視窗中，設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>或<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>。  
  
### <a name="to-change-the-layout-at-run-time"></a>若要在執行階段變更版面配置  
  
1.  將下列程式碼新增至按鈕或功能表`Click`事件處理常式：  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  在大部分情況下，您會想要新增如下所示的範例 > 一節，來調整大小的程式碼<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>和重新排列控制項，以配合新的方向。  
  
## <a name="example"></a>範例  
 下列範例示範如何回應<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged>事件處理常式中的事件。 此範例中，您需要<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，名為`DataRepeater1`表單，而且該它<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>包含兩個<xref:System.Windows.Forms.TextBox>控制項，名為`TextBox1`和`TextBox2`。  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [如何：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
