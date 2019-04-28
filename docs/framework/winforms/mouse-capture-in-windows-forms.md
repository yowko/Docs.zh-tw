---
title: Windows Form 中的滑鼠捕捉
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 30432c6978f60cc9ad47d5df5dafc7aa45229f3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800954"
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Form 中的滑鼠捕捉
*將滑鼠擷取*指的是當控制項接受所有的滑鼠輸入的命令。 當控制項已捕捉滑鼠時，會收到滑鼠輸入，在指標位於其框線內也一樣。  
  
## <a name="setting-mouse-capture"></a>設定滑鼠捕捉  
 在 Windows Form 中將滑鼠擷取控制項時，使用者按下滑鼠按鈕控制項，以及當使用者放開滑鼠按鈕時，放開滑鼠控制項。  
  
 <xref:System.Windows.Forms.Control.Capture%2A>屬性<xref:System.Windows.Forms.Control>類別可讓您指定控制項是否捕捉滑鼠。 若要判斷控制項遺失滑鼠捕捉時，處理<xref:System.Windows.Forms.Control.MouseCaptureChanged>事件。  
  
 前景視窗可以捕捉滑鼠。 當背景視窗嘗試要捕捉滑鼠時，視窗會收到滑鼠指標位於視窗的可見部分時，會發生的滑鼠事件的訊息。 此外，即使前景視窗已捕捉滑鼠，使用者仍然可以按一下另一個視窗中，將其帶至前景。 捕捉到滑鼠之後，快速鍵無法運作。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
