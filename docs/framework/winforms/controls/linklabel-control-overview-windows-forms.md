---
title: LinkLabel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745219"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.LinkLabel> 控制項可讓您將 Web 樣式的連結新增至 Windows Forms 應用程式。 您可以針對可以使用 <xref:System.Windows.Forms.Label> 控制項的所有專案使用 <xref:System.Windows.Forms.LinkLabel> 控制項;您也可以將部分文字設定為檔案、資料夾或網頁的連結。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>您可以使用 LinkLabel 控制項執行的動作  
 除了 <xref:System.Windows.Forms.Label> 控制項的所有屬性、方法和事件之外，<xref:System.Windows.Forms.LinkLabel> 控制項也具有超連結和連結色彩的屬性。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性會設定啟動連結之文字的區域。 [<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>]、[<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>] 和 [<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>] 屬性會設定連結的色彩。 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件會決定當選取連結文字時，會發生什麼事。  
  
 <xref:System.Windows.Forms.LinkLabel> 控制項最簡單的用法是使用 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性來顯示單一連結，但您也可以使用 <xref:System.Windows.Forms.LinkLabel.Links%2A> 屬性來顯示多個超連結。 <xref:System.Windows.Forms.LinkLabel.Links%2A> 屬性可讓您存取連結的集合。 您也可以在每個個別 <xref:System.Windows.Forms.LinkLabel.Link> 物件的 <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> 屬性中指定資料。 <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> 屬性的值可以用來儲存要顯示的檔案位置或網站的位址。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.LinkLabel>
- [Label 控制項概觀](label-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [操作說明：變更 Windows Forms LinkLabel 控制項的外觀](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
