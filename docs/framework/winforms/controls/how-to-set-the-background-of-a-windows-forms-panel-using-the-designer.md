---
title: "如何：使用設計工具設定 Windows Form 面板的背景"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 995dd5982601ba92a2ec23b82acd7131db183835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>如何：使用設計工具設定 Windows Form 面板的背景
Windows Form<xref:System.Windows.Forms.Panel>控制項可以顯示的背景色彩和背景影像。 <xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含在面板中，例如標籤和選項按鈕控制項的背景色彩。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未設定屬性，<xref:System.Windows.Forms.Control.BackColor%2A>選取項目將會填滿所有面板。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性設定，會在 [面板] 中所包含的控制項後面顯示的影像。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.Panel>控制項。 如需如何設定這類專案的資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>在 Windows Form 設計工具中設定背景  
  
1.  選取 <xref:System.Windows.Forms.Panel> 控制項。  
  
2.  在**屬性**視窗中，按一下箭號按鈕的下的一步<xref:System.Windows.Forms.Control.BackColor%2A>屬性來顯示具有三個索引標籤的視窗。  
  
3.  選取**自訂**索引標籤，顯示色的調色盤。  
  
4.  選取**Web**或**系統**索引標籤上顯示預先定義的色彩名稱清單，然後選取色彩。  
  
5.  在**屬性**視窗中，按一下箭號按鈕的下的一步<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。  
  
6.  在**開啟**對話方塊方塊中，選取您想要顯示的檔案。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
