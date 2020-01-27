---
title: 變更 TabControl 的外觀
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
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746606"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>如何：變更 Windows Form TabControl 的外觀
您可以使用 <xref:System.Windows.Forms.TabControl> 的屬性，以及組成控制項上個別索引標籤的 <xref:System.Windows.Forms.TabPage> 物件，來變更 Windows Forms 中索引標籤的外觀。 藉由設定這些屬性，您可以在索引標籤上顯示影像、以垂直方式顯示索引標籤，而不是水準地顯示索引標籤，以及啟用或停用 tab 鍵。  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>若要在索引標籤的 label 部分顯示圖示  
  
1. 將 <xref:System.Windows.Forms.ImageList> 控制項新增至表單。  
  
2. 將影像新增至影像清單。  
  
     如需影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[如何：使用 Windows Forms ImageList 元件來新增或移除影像](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
3. 將 <xref:System.Windows.Forms.TabControl> 的 [<xref:System.Windows.Forms.TabControl.ImageList%2A>] 屬性設定為 [<xref:System.Windows.Forms.ImageList>] 控制項。  
  
4. 將 <xref:System.Windows.Forms.TabPage> 的 <xref:System.Windows.Forms.TabPage.ImageIndex%2A> 屬性設定為清單中適當影像的索引。  
  
### <a name="to-create-multiple-rows-of-tabs"></a>若要建立多個資料列的索引標籤  
  
1. 新增您想要的索引標籤頁面數目。  
  
2. 將 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Multiline%2A> 屬性設定為 [`true`]。  
  
3. 如果索引標籤尚未出現在多個資料列中，請將 <xref:System.Windows.Forms.TabControl> 的 [<xref:System.Windows.Forms.Control.Width%2A>] 屬性設定為比所有索引標籤更窄。  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>排列控制項側邊的索引標籤  
  
- 將 <xref:System.Windows.Forms.TabControl> 的 [<xref:System.Windows.Forms.TabControl.Alignment%2A>] 屬性設定為 [<xref:System.Windows.Forms.TabAlignment.Left>] 或 [<xref:System.Windows.Forms.TabAlignment.Right>]。  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>以程式設計方式啟用或停用索引標籤上的所有控制項  
  
1. 將 <xref:System.Windows.Forms.TabPage> 的 [<xref:System.Windows.Forms.TabPage.Enabled%2A>] 屬性設定為 [`true`] 或 [`false`]。  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>將索引標籤顯示為按鈕  
  
- 將 <xref:System.Windows.Forms.TabControl> 的 [<xref:System.Windows.Forms.TabControl.Appearance%2A>] 屬性設定為 [<xref:System.Windows.Forms.TabAppearance.Buttons>] 或 [<xref:System.Windows.Forms.TabAppearance.FlatButtons>]。  
  
## <a name="see-also"></a>請參閱

- [TabControl 控制項](tabcontrol-control-windows-forms.md)
- [TabControl 控制項概觀](tabcontrol-control-overview-windows-forms.md)
- [操作說明：將控制項加入至索引標籤頁](how-to-add-a-control-to-a-tab-page.md)
- [操作說明：停用索引標籤頁](how-to-disable-tab-pages.md)
- [操作說明：使用 Windows Forms TabControl 加入和移除索引標籤](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
