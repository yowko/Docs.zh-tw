---
title: "LinkLabel 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73bbd04b9ef5d2d0c5457dafb794435b3a4db380
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.LinkLabel>控制項可讓您將 Web 樣式連結新增至 Windows Form 應用程式。 您可以使用<xref:System.Windows.Forms.LinkLabel>控制項，您可以使用的所有項目<xref:System.Windows.Forms.Label>控制; 您也可以設定部分文字的檔案、 資料夾或 Web 網頁的連結。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>您可以使用達成 LinkLabel 控制項  
 除了所有屬性、 方法和事件的<xref:System.Windows.Forms.Label>控制項，<xref:System.Windows.Forms.LinkLabel>控制項具有超連結和連結的色彩屬性。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性設定會啟用連結的文字區域。 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>，和<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>屬性設定為連結的色彩。 <xref:System.Windows.Forms.LinkLabel.LinkClicked>事件決定選取的連結文字時，會發生什麼事。  
  
 使用的最簡單的<xref:System.Windows.Forms.LinkLabel>控制項是顯示單一連結使用<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性，但是您也可以顯示多個超連結使用<xref:System.Windows.Forms.LinkLabel.Links%2A>屬性。 <xref:System.Windows.Forms.LinkLabel.Links%2A>屬性可讓您存取的連結集合。 您也可以指定在資料<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性的每個個別<xref:System.Windows.Forms.LinkLabel.Link>物件。 值<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性可以用來儲存要顯示之檔案的位置或網站的位址。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.LinkLabel>  
 [Label 控制項概觀](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [操作說明：變更 Windows Forms LinkLabel 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
