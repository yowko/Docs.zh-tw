---
title: LinkLabel 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 541467b0f1285d372e5f6d502d9d8f28c8c6333e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012954"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.LinkLabel>控制項可讓您將 Web 樣式連結新增至 Windows Forms 應用程式。 您可以使用<xref:System.Windows.Forms.LinkLabel>控制項，您可以使用的所有項目<xref:System.Windows.Forms.Label>控制; 您也可以設定文字的一部分為檔案、 資料夾或 Web 網頁的連結。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>您可以執行使用 LinkLabel 控制項  
 除了所有屬性、 方法和事件<xref:System.Windows.Forms.Label>控制項，<xref:System.Windows.Forms.LinkLabel>控制項有屬性的超連結和連結的色彩。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性設定會啟用連結的文字區域。 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>，和<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>屬性設定為連結的色彩。 <xref:System.Windows.Forms.LinkLabel.LinkClicked>事件可讓您判斷選取的連結文字時，會發生什麼事。  
  
 最簡單的用法<xref:System.Windows.Forms.LinkLabel>控制項是顯示單一連結，使用<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性，但您也可以顯示多個超連結使用<xref:System.Windows.Forms.LinkLabel.Links%2A>屬性。 <xref:System.Windows.Forms.LinkLabel.Links%2A>屬性可讓您存取連結的集合。 您也可以指定中的資料<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性的每個個別<xref:System.Windows.Forms.LinkLabel.Link>物件。 值<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性可以用來儲存要顯示之檔案的位置或網站的位址。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.LinkLabel>
- [Label 控制項概觀](label-control-overview-windows-forms.md)
- [如何：連結的物件，或使用 Windows Forms LinkLabel 控制項的網頁](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [如何：變更 Windows Forms LinkLabel 控制項的外觀](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
