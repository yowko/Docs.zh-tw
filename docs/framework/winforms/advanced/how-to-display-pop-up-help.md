---
title: "如何：顯示快顯說明"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5f57e0a7981e8cae93960c8ffc3ed2168594cf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-pop-up-help"></a>如何：顯示快顯說明
Windows Form 上顯示說明的其中一種方式是透過**協助**位於標題列，可透過存取右側的按鈕<xref:System.Windows.Forms.Form.HelpButton%2A>屬性。 這種顯示 [說明] 的方式非常適合與對話方塊一起使用。 以強制回應方式 (使用 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法) 顯示的對話方塊無法啟動外部 [說明] 系統，因為將焦點轉換至另一個視窗之前，必須先關閉強制回應對話方塊。 此外，使用**協助**按鈕需要有沒有**最小化**按鈕或**最大化**標題列中顯示的按鈕。 這是標準的對話方塊慣例，而表單則通常具有**最小化**和**最大化**按鈕。  
  
 請注意，您也可以使用 <xref:System.Windows.Forms.HelpProvider> 元件將控制項連結至 [說明] 系統中的檔案，即使您已實作快顯 [說明] 亦然。 如需詳細資訊，請參閱[Windows 應用程式中提供說明](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-display-pop-up-help"></a>顯示快顯說明  
  
1.  拖曳[HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)元件從 [工具箱] 加入至表單。  
  
     該元件會位於 Windows Form 設計工具底部的系統匣中。  
  
2.  在 [屬性] 視窗中，將 <xref:System.Windows.Forms.Form.HelpButton%2A> 屬性設定為 `true`。 表單的標題列右側會顯示一個有問號的按鈕。  
  
3.  為了顯示 <xref:System.Windows.Forms.Form.HelpButton%2A>，您必須將表單的 <xref:System.Windows.Forms.Form.MinimizeBox%2A> 和 <xref:System.Windows.Forms.Form.MaximizeBox%2A> 屬性設定為 `false`；將 <xref:System.Windows.Forms.Form.ControlBox%2A> 屬性設定為 `true`；並將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為下列其中一個值：<xref:System.Windows.Forms.FormBorderStyle.FixedSingle>、<xref:System.Windows.Forms.FormBorderStyle.Fixed3D>、<xref:System.Windows.Forms.FormBorderStyle.FixedDialog> 或 <xref:System.Windows.Forms.FormBorderStyle.Sizable>。  
  
4.  選取您要在表單上顯示 [說明] 的控制項，並在 [屬性] 視窗中設定 [說明] 字串。 這是將類似的視窗中顯示的文字字串[工具提示](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)。  
  
5.  請按 **F5**。  
  
6.  按**協助**按鈕標題列上，按一下的控制項，供您設定的說明字串。  
  
## <a name="see-also"></a>另請參閱  
 [使用工具提示來顯示控制項說明](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [整合 Windows Forms 中的使用者說明](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
