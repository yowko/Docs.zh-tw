---
title: 選取 Windows Form Button 控制項的方法
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: f2881646a05d257044c6461f822a4c35a225f8c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759839"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>選取 Windows Form Button 控制項的方法
將 Windows Form 按鈕可以下列方式選取：  
  
- 使用滑鼠按一下的按鈕。  
  
- 叫用按鈕的<xref:System.Windows.Forms.Control.Click>在程式碼中的事件。  
  
- 藉由按下 TAB 鍵，將焦點移至 按鈕，然後選擇該按鈕按下空格鍵或 ENTER 鍵。  
  
- 按下便捷鍵 （ALT + 加底線的字母） 按鈕。 如需存取金鑰的詳細資訊，請參閱[How to:建立 Windows form 控制項的便捷鍵](how-to-create-access-keys-for-windows-forms-controls.md)。  
  
- 如果表單的 接受 按鈕的按鈕，按下 ENTER 鍵會選擇該按鈕，即使另一個控制項有焦點，但如果控制項是另一個按鈕、 多行文字 方塊中或自訂控制項的設陷 enter 鍵。  
  
- 如果按鈕是 「 取消 」 按鈕的表單，按下 esc 鍵會選擇 [] 按鈕，即使另一個控制項有焦點。  
  
- 呼叫<xref:System.Windows.Forms.Button.PerformClick%2A>方法來以程式設計方式選取的按鈕。  
  
## <a name="see-also"></a>另請參閱

- [Button 控制項概觀](button-control-overview-windows-forms.md)
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [Button 控制項](button-control-windows-forms.md)
