---
title: "如何：使用設計工具設定由 Windows Form 控制項所顯示的文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6d49466e5dd25bbe9e97262d68f2c3fb2f8ba1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>如何：使用設計工具設定由 Windows Form 控制項所顯示的文字
Windows Form 控制項通常會顯示控制項的主要功能與相關的文字。 例如，<xref:System.Windows.Forms.Button>控制項通常會顯示表示按下按鈕時，將會執行什麼動作的標題。 針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。 您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>若要設定文字和字型與設計工具  
  
1.  在 [屬性] 視窗中，設定<xref:System.Windows.Forms.Control.Text%2A>要適當的字串控制項屬性。  
  
     若要建立加底線的快速鍵，包括連字號 (&) 會成為快顯索引鍵的字母前面。  
  
2.  在 [屬性] 視窗中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.Control.Font%2A>屬性。  
  
     在標準的字型 對話方塊中，選取您想要的字型、 字型樣式、 大小、 效果 （例如刪除線或底線） 和指令碼。  
  
## <a name="see-also"></a>請參閱  
 [操作說明：設定由 Windows Forms 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
