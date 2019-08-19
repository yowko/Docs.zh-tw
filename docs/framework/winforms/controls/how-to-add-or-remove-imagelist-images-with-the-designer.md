---
title: HOW TO：使用設計工具新增或移除 ImageList 影像
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 63692a797ad49f0adc3a0c5b0bfff1aebbc65257
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038274"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>HOW TO：使用設計工具新增或移除 ImageList 影像

您可以使用幾種不同<xref:System.Windows.Forms.ImageList>的方式將影像新增至元件。 您可以使用與<xref:System.Windows.Forms.ImageList>相關聯的智慧標籤非常快速地新增影像, 或者<xref:System.Windows.Forms.ImageList>, 如果您要在上設定數個其他屬性, 您可能會發現使用屬性視窗新增影像會比較方便。 您也可以使用程式碼來新增影像。 如需如何使用程式碼加入影像的詳細資訊, [請參閱如何:使用 Windows Forms ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)來新增或移除映射。 通常, 您會<xref:System.Windows.Forms.ImageList>在元件與控制項建立關聯之前, 先將影像填入其中, 但這不是必要的。


### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>若要使用屬性視窗來新增或移除映射

1. <xref:System.Windows.Forms.ImageList>選取元件, 或將它新增至表單。

2. 在 屬性視窗中, 按一下![ <xref:System.Windows.Forms.ImageList.Images%2A>屬性旁邊的省略號按鈕 (](./media/visual-studio-ellipsis-button.png)Visual Studio 的屬性視窗中的省略號按鈕 (...))。

3. 在**影像集合編輯器**，按一下 **新增**或**移除**新增或移除清單中的映像。

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>使用智慧標籤新增或移除影像

1. <xref:System.Windows.Forms.ImageList>選取元件, 或將它新增至表單。

2. 按一下智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))

3. 在 [ **ImageList**工作] 對話方塊中, 選取 **[選擇影像**]。

4. 在 [ **Images] 集合編輯器**中, 按一下 [**新增**] 或 [**移除**], 從清單中新增或移除映射。

## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](../advanced/images-bitmaps-and-metafiles.md)
- [逐步解說：在 Windows Forms 控制項上使用智慧標籤執行一般工作](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [ImageList 元件](imagelist-component-windows-forms.md)
