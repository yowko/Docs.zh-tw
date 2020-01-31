---
title: 選取按鈕控制項的方式
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740012"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>選取 Windows Form Button 控制項的方法
您可以透過下列方式選取 [Windows Forms] 按鈕：  
  
- 使用滑鼠按一下按鈕。  
  
- 在程式碼中叫用按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
- 按下 TAB 鍵將焦點移至按鈕，然後按空格鍵或 ENTER 以選擇按鈕。  
  
- 按下按鈕的存取金鑰（ALT + 加底線的字母）。 如需存取金鑰的詳細資訊，請參閱[如何：建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)。  
  
- 如果按鈕是表單的 [接受] 按鈕，按 ENTER 鍵會選擇按鈕，即使另一個控制項有焦點也一樣，除非該其他控制項是另一個按鈕、多行文字方塊或自訂控制項，它會陷印 ENTER 鍵。  
  
- 如果按鈕是表單的 [取消] 按鈕，按 ESC 鍵會選擇按鈕，即使另一個控制項有焦點也一樣。  
  
- 呼叫 <xref:System.Windows.Forms.Button.PerformClick%2A> 方法，以程式設計方式選取按鈕。  
  
## <a name="see-also"></a>請參閱

- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [操作說明：回應 Windows Forms Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [Button 控制項](button-control-windows-forms.md)
