---
title: HOW TO：使用設計工具將 Windows Forms 的按鈕指定為取消按鈕
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: f127a1a74643c975aea73b24896c098b365aa327
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972298"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>HOW TO：使用設計工具將 Windows Forms 的按鈕指定為取消按鈕
在任何 Windows 表單上，您可以指定<xref:System.Windows.Forms.Button>設為 [取消] 按鈕的控制項。 每當使用者按下 ESC 鍵，不論哪一個表單上的其他控制項具有焦點時，按一下 [取消] 按鈕。 這類按鈕通常被設計成讓使用者快速結束作業，而不需要認可至任何動作。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-designate-the-cancel-button"></a>若要指定 [取消] 按鈕  
  
1. 選取的按鈕所在的表單。  
  
2. 在 [**屬性**] 視窗中，將表單的<xref:System.Windows.Forms.Form.CancelButton%2A>屬性設<xref:System.Windows.Forms.Button>控制項的名稱。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [如何：將 Windows Form 按鈕指定為接受按鈕使用設計工具](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
