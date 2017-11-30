---
title: "使用鍵盤事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19bad48188a039baeeb6365a2cd38671f83fca4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-keyboard-events"></a>使用鍵盤事件
大部分的 Windows Form 程式藉由處理鍵盤事件來處理鍵盤輸入。 本主題提供鍵盤事件的概觀，包含何時使用每個事件的詳細資訊，以及提供給每個事件的資料。  另請參閱[事件處理常式概觀 (Windows Form)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\))，[事件概觀 (Windows Form)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))。  
  
## <a name="keyboard-events"></a>鍵盤事件  
 Windows Form 提供兩個在使用者按下鍵盤按鍵時會發生的事件，也提供一個當使用者鬆開鍵盤按鍵時會發生的事件：  
  
-   <xref:System.Windows.Forms.Control.KeyDown> 事件會發生一次  
  
-   當使用者按住相同按鍵時，<xref:System.Windows.Forms.Control.KeyPress> 事件可以發生多次。  
  
-   當使用者鬆開按鍵，就會發生 <xref:System.Windows.Forms.Control.KeyUp> 事件一次。  
  
 當使用者按下按鍵時，Windows Form 會依據鍵盤訊息指定字元鍵或實體鍵來決定要引發哪個事件。 如需字元和實體索引鍵的詳細資訊，請參閱[鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)。  
  
 下表描述這三個鍵盤事件。  
  
|鍵盤事件|描述|結果|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|當使用者按下實體鍵時，會引發這個事件。|<xref:System.Windows.Forms.Control.KeyDown> 的處理常式會接收：<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs> 參數，提供 <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> 屬性 (可指定實體鍵盤按鈕)。</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> 屬性 (SHIFT、CTRL 或 ALT)。</li><li><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> 屬性 (會結合按鍵碼和修飾詞)。 <xref:System.Windows.Forms.KeyEventArgs> 參數也會提供：<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.Handled%2A> 屬性，可設定防止基礎控制項接收按鍵。</li><li><xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> 屬性，可用來隱藏該按鍵動作的 <xref:System.Windows.Forms.Control.KeyPress> 和 <xref:System.Windows.Forms.Control.KeyUp> 事件。</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|當已按下的一個或更多按鍵產生字元時，會引發這個事件。 例如，使用者按下 SHIFT 和小寫 "a" 按鍵，會產生大寫字母的 "A" 字元。|在 <xref:System.Windows.Forms.Control.KeyDown> 之後會引發 <xref:System.Windows.Forms.Control.KeyPress>。<br /><br /> <ul><li><xref:System.Windows.Forms.Control.KeyPress> 的處理常式會接收：</li><li><xref:System.Windows.Forms.KeyPressEventArgs> 參數，其中包含已按下按鍵的字元碼。 對於每種字元鍵和輔助按鍵的組合而言，此字元碼是唯一的。<br /><br />     例如，"A" 按鍵會產生：<br /><br /> <ul><li>若與 SHIFT 鍵一同按下，則產生字元碼 65，</li><li>若 CAPS LOCK 鍵已開啟且只按下它，則產生 97，</li><li>若與 CTRL 鍵一同按下，則產生 1。</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|當使用者鬆開實體鍵時，會引發這個事件。|<xref:System.Windows.Forms.Control.KeyUp> 的處理常式會接收：<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs> 參數：<br /><br /> <ul><li>提供 <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> 屬性 (可指定實體鍵盤按鈕)。</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> 屬性 (SHIFT、CTRL 或 ALT)。</li><li><xref:System.Globalization.SortKey.KeyData%2A> 屬性 (會結合按鍵碼和修飾詞)。</li></ul></li></ul>|  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 應用程式中的鍵盤輸入](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
