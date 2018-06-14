---
title: 如何：變更 Windows Form TabControl 的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 1ea2208229d790f69e517d55e2de5ee042bdfb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531036"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>如何：變更 Windows Form TabControl 的外觀
您可以使用的屬性，以變更 Windows Form 中的索引標籤的外觀<xref:System.Windows.Forms.TabControl>和<xref:System.Windows.Forms.TabPage>組成個別的索引標籤控制項上的物件。 藉由設定這些屬性，您可以顯示索引標籤上的映像、 顯示垂直而非水平索引標籤、 顯示多個資料列的索引標籤，和啟用或以程式設計的方式停用索引標籤。  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>標籤組件的索引標籤上顯示圖示  
  
1.  新增<xref:System.Windows.Forms.ImageList>控制項加入表單。  
  
2.  將影像加入至映像清單。  
  
     如需影像清單的詳細資訊，請參閱[ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)和[如何： 加入或移除映像使用 Windows Form ImageList 元件](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
3.  設定<xref:System.Windows.Forms.TabControl.ImageList%2A>屬性<xref:System.Windows.Forms.TabControl>至<xref:System.Windows.Forms.ImageList>控制項。  
  
4.  設定<xref:System.Windows.Forms.TabPage.ImageIndex%2A>屬性<xref:System.Windows.Forms.TabPage>為適當的映像清單中的索引。  
  
### <a name="to-create-multiple-rows-of-tabs"></a>若要建立多個資料列的索引標籤  
  
1.  新增您想要的索引標籤頁的數目。  
  
2.  設定<xref:System.Windows.Forms.TabControl.Multiline%2A>屬性<xref:System.Windows.Forms.TabControl>至`true`。  
  
3.  如果索引標籤已經不在多個資料列，設定<xref:System.Windows.Forms.Control.Width%2A>屬性<xref:System.Windows.Forms.TabControl>為窄比所有索引標籤。  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>若要排列控制項的側邊的索引標籤  
  
-   設定<xref:System.Windows.Forms.TabControl.Alignment%2A>屬性<xref:System.Windows.Forms.TabControl>至<xref:System.Windows.Forms.TabAlignment.Left>或<xref:System.Windows.Forms.TabAlignment.Right>。  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>以程式設計方式啟用或停用索引標籤上的所有控制項  
  
1.  設定<xref:System.Windows.Forms.TabPage.Enabled%2A>屬性<xref:System.Windows.Forms.TabPage>至`true`或`false`。  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>若要為按鈕會顯示索引標籤  
  
-   設定<xref:System.Windows.Forms.TabControl.Appearance%2A>屬性<xref:System.Windows.Forms.TabControl>至<xref:System.Windows.Forms.TabAppearance.Buttons>或<xref:System.Windows.Forms.TabAppearance.FlatButtons>。  
  
## <a name="see-also"></a>另請參閱  
 [TabControl 控制項](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [操作說明：將控制項加入至索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [操作說明：停用索引標籤頁](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [操作說明：使用 Windows Forms TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
