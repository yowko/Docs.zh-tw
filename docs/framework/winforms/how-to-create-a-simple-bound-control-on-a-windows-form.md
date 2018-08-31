---
title: 如何：在 Windows Form 上建立簡單繫結控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 26bc136ea2b7e5bda4a57c5dad65ec3522efcd3d
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258717"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>如何：在 Windows Form 上建立簡單繫結控制項
具有*簡單繫結*，您可以在控制項中顯示單一資料元素，例如資料集資料表中的資料行值。 您可以簡單繫結控制項的任何屬性的資料值。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-simple-bind-a-control"></a>以簡單繫結控制項  
  
1.  連接至資料來源。 如需詳細資訊，請參閱 <<c0> [ 連接到資料來源](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)。  
  
2.  在表單中，選取控制項，並顯示**屬性**視窗。  
  
3.  依序展開 **(DataBindings)** 屬性。  
  
     最常繫結的屬性會顯示底下 **(DataBindings)** 屬性。 例如，在大部分的控制項**文字**屬性最常繫結。  
  
4.  如果您想要將屬性繫結不是其中一個常見的繫結的屬性，請按一下**省略符號** 按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 中 **（進階）** 方塊，以顯示**格式化與進階繫結**該控制項屬性的對話方塊中的完整清單。  
  
5.  選取您想要繫結，然後按一下下方的下拉式箭頭的屬性**繫結**。  
  
     會顯示可用資料來源清單。  
  
6.  展開您想要繫結的資料來源，直到您找到您要的單一資料項目。 例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。  
  
7.  按一下要繫結項目的名稱。  
  
8.  如果您正在處理**格式化與進階繫結** 對話方塊中，按一下**確定**返回**屬性**視窗。  
  
9. 如果您想要繫結控制項的其他屬性，請重複步驟 3 到 7。  
  
    > [!NOTE]
    >  由於簡單繫結控制項顯示單一資料元素，就經常包含 Windows 表單以簡單繫結控制項中的 瀏覽邏輯。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Binding>  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
