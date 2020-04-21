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
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739514"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel 控制項概觀 (Windows Form)
Windows 表<xref:System.Windows.Forms.LinkLabel>單元件允許您向 Windows 窗體應用程式添加 Web 樣式的連結。 您可以將控制項<xref:System.Windows.Forms.LinkLabel>用於可<xref:System.Windows.Forms.Label>用於控制件的所有內容;還可以將文本的一部分設置為指向檔、資料夾或網頁的連結。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>使用連結標籤控制項可以做什麼  
 除了<xref:System.Windows.Forms.Label>控制式所有屬性、方法和事件外,<xref:System.Windows.Forms.LinkLabel>控制項還具有超連結和連結顏色的屬性。 屬性<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>設置啟動連結的文本區域。 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>屬性設置<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>連結的顏色。 該<xref:System.Windows.Forms.LinkLabel.LinkClicked>事件確定選擇連結文本時會發生什麼情況。  
  
 控制項最簡單的用處<xref:System.Windows.Forms.LinkLabel>是使用<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性 顯示單個連結,但<xref:System.Windows.Forms.LinkLabel.Links%2A>也可以使用 屬性 顯示多個超連結。 該<xref:System.Windows.Forms.LinkLabel.Links%2A>屬性使您能夠訪問連結的集合。 您還可以在每個單個<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A><xref:System.Windows.Forms.LinkLabel.Link>物件的屬性中指定數據。 <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性的值可用於存儲要顯示的檔案的位置或網站的位址。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.LinkLabel>
- [Label 控制項概觀](label-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [操作說明：變更 Windows Forms LinkLabel 控制項的外觀](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
