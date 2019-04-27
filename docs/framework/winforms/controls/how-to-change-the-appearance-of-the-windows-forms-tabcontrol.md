---
title: HOW TO：變更 Windows Forms TabControl 的外觀
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
ms.openlocfilehash: 05df05a52914f27a4b62cf7bde92e5d942b6ea06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904263"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>HOW TO：變更 Windows Forms TabControl 的外觀
您可以使用的屬性來變更 Windows Form 中的索引標籤的外觀<xref:System.Windows.Forms.TabControl>而<xref:System.Windows.Forms.TabPage>組成控制項的個別索引標籤的物件。 藉由設定這些屬性，，您可以索引標籤上顯示的映像、 顯示垂直方式而非水平索引標籤，顯示多個資料列的索引標籤，並啟用或以程式設計方式停用索引標籤。  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>標籤組件的索引標籤上顯示圖示  
  
1. 新增<xref:System.Windows.Forms.ImageList>控制項加入表單。  
  
2. 將影像新增至映像清單中。  
  
     如需有關影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[How to:新增或移除映像的 Windows Form ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
3. 設定<xref:System.Windows.Forms.TabControl.ImageList%2A>的屬性<xref:System.Windows.Forms.TabControl>到<xref:System.Windows.Forms.ImageList>控制項。  
  
4. 設定<xref:System.Windows.Forms.TabPage.ImageIndex%2A>屬性<xref:System.Windows.Forms.TabPage>至適當的映像清單中的索引。  
  
### <a name="to-create-multiple-rows-of-tabs"></a>若要建立多個資料列的索引標籤  
  
1. 新增您想要的索引標籤頁的數目。  
  
2. 設定<xref:System.Windows.Forms.TabControl.Multiline%2A>的屬性<xref:System.Windows.Forms.TabControl>至`true`。  
  
3. 如果索引標籤已經不在多個資料列，設定<xref:System.Windows.Forms.Control.Width%2A>屬性<xref:System.Windows.Forms.TabControl>要比所有索引標籤還窄。  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>若要排列控制項旁邊的索引標籤  
  
-   設定<xref:System.Windows.Forms.TabControl.Alignment%2A>的屬性<xref:System.Windows.Forms.TabControl>要<xref:System.Windows.Forms.TabAlignment.Left>或<xref:System.Windows.Forms.TabAlignment.Right>。  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>以程式設計方式啟用或停用的索引標籤上的所有控制項  
  
1. 設定<xref:System.Windows.Forms.TabPage.Enabled%2A>的屬性<xref:System.Windows.Forms.TabPage>要`true`或`false`。  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>若要顯示為按鈕的索引標籤  
  
-   設定<xref:System.Windows.Forms.TabControl.Appearance%2A>的屬性<xref:System.Windows.Forms.TabControl>要<xref:System.Windows.Forms.TabAppearance.Buttons>或<xref:System.Windows.Forms.TabAppearance.FlatButtons>。  
  
## <a name="see-also"></a>另請參閱

- [TabControl 控制項](tabcontrol-control-windows-forms.md)
- [TabControl 控制項概觀](tabcontrol-control-overview-windows-forms.md)
- [如何：將控制項加入索引標籤頁](how-to-add-a-control-to-a-tab-page.md)
- [如何：停用索引標籤頁](how-to-disable-tab-pages.md)
- [如何：新增和移除使用 Windows Form TabControl 的索引標籤](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
