---
title: HOW TO：使用設計工具將 Windows Forms 的按鈕指定為接受按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: e0eaa90c8450888ea325470db5d4adae555f8d82
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304164"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>HOW TO：使用設計工具將 Windows Forms 的按鈕指定為接受按鈕
在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為接受按鈕，也就是預設按鈕的控制項。 每當使用者按下 ENTER 鍵，不論哪一個表單上的其他控制項具有焦點按一下預設按鈕。 例外狀況是另一個按鈕具有焦點的控制項時，會被按一下的按鈕，並將焦點放在此情況下，-多行文字方塊中或自訂控制項的設陷 ENTER 鍵。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-designate-the-accept-button"></a>若要指定為接受按鈕  
  
1. 選取的按鈕所在的表單。  
  
2. 在 [**屬性**] 視窗中，將表單的<xref:System.Windows.Forms.Form.AcceptButton%2A>屬性設<xref:System.Windows.Forms.Button>控制項的名稱。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：將 Windows Form 按鈕指定為取消按鈕使用設計工具](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
