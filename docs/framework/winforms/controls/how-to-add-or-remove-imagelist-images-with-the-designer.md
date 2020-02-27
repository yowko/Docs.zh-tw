---
title: 如何：使用設計工具加入或移除 ImageList 影像
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628718"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>如何：使用設計工具加入或移除 ImageList 影像

您可以使用幾種不同的方式，將影像新增至 <xref:System.Windows.Forms.ImageList> 元件。 您可以使用與 <xref:System.Windows.Forms.ImageList>相關聯的智慧標籤非常快速地新增影像，或者，如果您要在 <xref:System.Windows.Forms.ImageList>上設定數個其他屬性，您可能會發現使用屬性視窗來新增影像會更方便。 您也可以使用程式碼來新增影像。 如需如何使用程式碼加入影像的詳細資訊，請參閱[如何：使用 Windows Forms ImageList 元件來新增或移除映射](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。 通常，您會先使用影像填入 <xref:System.Windows.Forms.ImageList> 元件，再將其與控制項建立關聯，但這不是必要的。

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>若要使用屬性視窗來新增或移除映射

1. 選取 [<xref:System.Windows.Forms.ImageList>] 元件，或在表單中加入一個。

2. 在 [屬性視窗中，按一下 [](./media/visual-studio-ellipsis-button.png)] 屬性旁邊的省略號按鈕（!Visual Studio 的屬性視窗中的省略號按鈕（...）。<xref:System.Windows.Forms.ImageList.Images%2A>

3. 在 [**映射集合編輯器**] 中，按一下 [**新增**] 或 [**移除**]，從清單中新增或移除影像。

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>使用智慧標籤新增或移除影像

1. 選取 [<xref:System.Windows.Forms.ImageList>] 元件，或在表單中加入一個。

2. 按一下設計工具動作圖像（![小型黑色箭號](./media/designer-actions-glyph.gif))

3. 在 [ **ImageList**工作] 對話方塊中，選取 **[選擇影像**]。

4. 在 [ **Images] 集合編輯器**中，按一下 [**新增**] 或 [**移除**]，從清單中新增或移除映射。

## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](../advanced/images-bitmaps-and-metafiles.md)
- [逐步解說：使用設計工具動作執行一般工作](perform-common-tasks-design-actions.md)
- [ImageList 元件](imagelist-component-windows-forms.md)
