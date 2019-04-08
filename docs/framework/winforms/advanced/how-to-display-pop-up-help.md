---
title: HOW TO：顯示快顯說明
ms.date: 03/30/2017
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
ms.openlocfilehash: f6b6fa0c111783dcdad0387aed7d40fb54fa7b26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078365"
---
# <a name="how-to-display-pop-up-help"></a>HOW TO：顯示快顯說明
若要在 Windows Form 上顯示說明的方法之一是透過**幫助**按鈕位於標題列，可透過存取右側<xref:System.Windows.Forms.Form.HelpButton%2A>屬性。 這種顯示 [說明] 的方式非常適合與對話方塊一起使用。 以強制回應方式 (使用 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法) 顯示的對話方塊無法啟動外部 [說明] 系統，因為將焦點轉換至另一個視窗之前，必須先關閉強制回應對話方塊。 此外，使用**幫助** 按鈕可讓您需要有沒有**最小化** 按鈕或**最大化**標題列中顯示的按鈕。 這是標準的對話方塊慣例，而表單則通常具有**最小化**並**最大化**按鈕。  
  
 請注意，您也可以使用 <xref:System.Windows.Forms.HelpProvider> 元件將控制項連結至 [說明] 系統中的檔案，即使您已實作快顯 [說明] 亦然。 如需詳細資訊，請參閱 < [Windows 應用程式中提供幫助](how-to-provide-help-in-a-windows-application.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-display-pop-up-help"></a>顯示快顯說明  
  
1.  拖曳[HelpProvider](../controls/helpprovider-component-windows-forms.md)元件從工具箱拖曳至表單。  
  
     該元件會位於 Windows Form 設計工具底部的系統匣中。  
  
2.  在 [屬性] 視窗中，將 <xref:System.Windows.Forms.Form.HelpButton%2A> 屬性設定為 `true`。 表單的標題列右側會顯示一個有問號的按鈕。  
  
3.  為了顯示 <xref:System.Windows.Forms.Form.HelpButton%2A>，您必須將表單的 <xref:System.Windows.Forms.Form.MinimizeBox%2A> 和 <xref:System.Windows.Forms.Form.MaximizeBox%2A> 屬性設定為 `false`；將 <xref:System.Windows.Forms.Form.ControlBox%2A> 屬性設定為 `true`；並將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為下列其中一個值：<xref:System.Windows.Forms.FormBorderStyle.FixedSingle>、<xref:System.Windows.Forms.FormBorderStyle.Fixed3D>、<xref:System.Windows.Forms.FormBorderStyle.FixedDialog> 或 <xref:System.Windows.Forms.FormBorderStyle.Sizable>。  
  
4.  選取您要在表單上顯示 [說明] 的控制項，並在 [屬性] 視窗中設定 [說明] 字串。 這是會在類似於視窗中顯示的文字字串[工具提示](../controls/tooltip-component-windows-forms.md)。  
  
5.  請按 **F5**。  
  
6.  按下**協助**按鈕標題列上，然後按一下您要在其設定的說明字串的控制項。  
  
## <a name="see-also"></a>另請參閱

- [使用工具提示來顯示控制項說明](control-help-using-tooltips.md)
- [整合 Windows Form 中的使用者說明](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
