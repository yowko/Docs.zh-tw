---
title: "Windows Form 中的滑鼠捕捉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Form 中的滑鼠捕捉
*將滑鼠擷取*指的是當控制項接受所有的滑鼠輸入的命令。 當控制項捕捉住滑鼠時，不論是否在指標位於其框線內接收滑鼠輸入。  
  
## <a name="setting-mouse-capture"></a>設定滑鼠捕捉  
 在 Windows Form 中將滑鼠擷取控制項時，使用者按下滑鼠按鈕控制項，以及當使用者放開滑鼠按鈕控制項放開滑鼠。  
  
 <xref:System.Windows.Forms.Control.Capture%2A>屬性<xref:System.Windows.Forms.Control>類別可讓您指定控制項是否捕捉住滑鼠。 若要判斷當控制項失去滑鼠擷取，請處理<xref:System.Windows.Forms.Control.MouseCaptureChanged>事件。  
  
 前景視窗可以捕捉滑鼠。 當背景視窗嘗試捕捉滑鼠時，視窗會收到滑鼠指標位於視窗的可見部分時發生的滑鼠事件的訊息。 此外，即使前景視窗已捕捉滑鼠，使用者仍然可以按一下另一個視窗中，將其帶至前景。 當滑鼠捕捉時，快速鍵無法運作。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
