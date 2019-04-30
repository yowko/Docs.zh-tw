---
title: ImageList 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: 9869e647613ccf009954a5d65445947fbced40e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971167"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList 元件概觀 (Windows Form)

Windows Form <xref:System.Windows.Forms.ImageList> 元件可用來儲存影像，然後可以用控制項來顯示這些影像。 影像清單可讓您針對單一且一致的影像目錄來撰寫程式碼。 例如，若要旋轉 <xref:System.Windows.Forms.Button> 控制項所顯示的影像，您只要變更按鈕的 <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> 或 <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> 屬性即可。 您也可以將相同的影像清單與多個控制項產生關聯。 例如，如果您同時使用 <xref:System.Windows.Forms.ListView> 控制項和 <xref:System.Windows.Forms.TreeView> 控制項來顯示相同的檔案清單，在影像清單中變更檔案的圖示將會導致新的圖示同時出現在這兩個檢視中。

## <a name="using-imagelist-with-controls"></a>使用 ImageList 搭配控制項

您可以使用影像清單來搭配具有 `ImageList` 屬性的任何控制項，或者若是 <xref:System.Windows.Forms.ListView> 控制項，則為 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 和 <xref:System.Windows.Forms.ListView.LargeImageList%2A> 屬性。 可與影像清單產生關聯的控制項包括：<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.ToolBar>、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.Label> 控制項。 若要將影像清單與控制項產生關聯，請將控制項的 `ImageList` 屬性設為 <xref:System.Windows.Forms.ImageList> 元件的名稱。

## <a name="key-properties"></a>索引鍵內容

<xref:System.Windows.Forms.ImageList> 元件的索引鍵屬性是 <xref:System.Windows.Forms.ImageList.Images%2A>，其中包含要供相關聯控制項使用的圖片。 每個個別影像都可以依其索引值或索引鍵來存取。 <xref:System.Windows.Forms.ImageList.ColorDepth%2A> 屬性可決定要用來呈現影像的色彩數目。 所有影像都會以 <xref:System.Windows.Forms.ImageList.ImageSize%2A> 屬性設定的相同大小來顯示。 較大的影像會調整為符合此大小。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ImageList>
- [如何：新增或移除映像使用 Windows Form ImageList 元件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)