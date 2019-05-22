---
title: 作法：使用設計工具新增或移除 ImageList 影像
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 57c124f19d208192cb2d4500274f7f897948252a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960150"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>HOW TO：使用設計工具新增或移除 ImageList 影像

您可以新增映像發佈至<xref:System.Windows.Forms.ImageList>元件數個不同的方式。 您可以使用相關聯的智慧標籤，非常快速地將影像<xref:System.Windows.Forms.ImageList>，或如果您要設定幾個其他屬性上<xref:System.Windows.Forms.ImageList>，您可能會發現它更方便地新增 [屬性] 視窗的影像。 您也可以使用程式碼，以新增映像。 如需有關新增程式碼使用的映像的詳細資訊，請參閱[How to:新增或移除映像的 Windows Form ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。 通常您填入<xref:System.Windows.Forms.ImageList>映像之前表單與控制項相關聯，但這不是必要元件。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>若要新增或移除映像，使用 [屬性] 視窗

1. 選取<xref:System.Windows.Forms.ImageList>元件，或新增至表單。

2. 在 [屬性] 視窗中，按一下 省略符號按鈕 (![的 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 旁邊<xref:System.Windows.Forms.ImageList.Images%2A>屬性。

3. 在**影像集合編輯器**，按一下 **新增**或**移除**新增或移除清單中的映像。

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>若要加入或移除使用智慧標籤的影像

1. 選取<xref:System.Windows.Forms.ImageList>元件，或新增至表單。

2. 按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))

3. 在  **ImageList 工作**對話方塊中，選取**選擇映像**。

4. 在  **Editor Kolekce Images**按一下 **新增**或**移除**新增或移除清單中的映像。

## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](../advanced/images-bitmaps-and-metafiles.md)
- [逐步解說：一般工作，使用智慧標籤執行 Windows Form 控制項](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [ImageList 元件](imagelist-component-windows-forms.md)
