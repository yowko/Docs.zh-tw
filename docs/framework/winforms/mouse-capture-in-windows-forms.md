---
title: 滑鼠捕捉
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741027"
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Form 中的滑鼠捕捉
*滑鼠捕捉*是指控制項取得所有滑鼠輸入的命令時。 當控制項捕捉到滑鼠時，不論指標是否在其框線內，它都會收到滑鼠輸入。  
  
## <a name="setting-mouse-capture"></a>設定滑鼠捕捉  
 在 Windows Forms 當使用者在控制項上按下滑鼠按鍵時，控制項會捕捉滑鼠，而當使用者放開滑鼠按鍵時，控制項就會放開滑鼠。  
  
 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.Capture%2A> 屬性會指定控制項是否已捕捉滑鼠。 若要判斷控制項何時失去滑鼠捕捉，請處理 <xref:System.Windows.Forms.Control.MouseCaptureChanged> 事件。  
  
 只有前景視窗可以捕捉滑鼠。 當背景視窗嘗試捕獲滑鼠時，只有當滑鼠指標位於視窗的可見部分內時，視窗才會收到滑鼠事件的訊息。 此外，即使前景視窗已捕捉過滑鼠，使用者仍然可以按一下另一個視窗，將其移至前景。 當您捕捉到滑鼠時，快速鍵無法正常執行。  
  
## <a name="see-also"></a>請參閱

- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
