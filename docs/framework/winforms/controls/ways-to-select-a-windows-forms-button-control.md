---
title: "選取 Windows Form Button 控制項的方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b5359446a80da257f5afec07cc70e3d4aad46b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>選取 Windows Form Button 控制項的方法
以下列方式，可以選取 Windows Form 按鈕：  
  
-   按一下按鈕，使用滑鼠。  
  
-   叫用按鈕的<xref:System.Windows.Forms.Control.Click>程式碼中的事件。  
  
-   按下 TAB 鍵，將焦點移至按鈕，然後選擇該按鈕按下空格鍵或 ENTER。  
  
-   按下便捷鍵 （ALT + 加底線的字母） 按鈕。 如需存取金鑰的詳細資訊，請參閱[How to： 建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。  
  
-   如果按鈕是 [接受] 按鈕的形式，按下 ENTER 鍵會選擇該按鈕，即使另一個控制項有焦點，除非控制項是另一個按鈕、 多行文字方塊中或自訂控制項的 enter 鍵。  
  
-   如果按鈕是表單的 「 取消 」 按鈕，按下 esc 鍵選擇該按鈕，即使另一個控制項有焦點。  
  
-   呼叫<xref:System.Windows.Forms.Button.PerformClick%2A>方法來以程式設計方式選取按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [操作說明：回應 Windows Forms Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
