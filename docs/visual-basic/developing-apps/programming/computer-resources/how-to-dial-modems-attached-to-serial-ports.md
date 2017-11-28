---
title: "如何：在 Visual Basic 中撥接與序列埠連接的數據機"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea1b2d6152af8919ac1aa272def4ba198b33867c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>如何：在 Visual Basic 中撥接與序列埠連接的數據機
本主題說明如何在 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 中使用 `My.Computer.Ports` 撥接數據機。  
  
 一般而言，數據機會連接至電腦上的其中一個序列埠。 您的應用程式必須將命令傳送至適當的序列埠，才能與數據機通訊。  
  
### <a name="to-dial-a-modem"></a>撥接數據機  
  
1.  判斷要將數據機連接至哪一個序列埠。 此範例假設數據機是在 COM1。  
  
2.  請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。  
  
     `Using` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。 所有管理序列埠的程式碼都應該出現在此區塊或 `Try...Catch...Finally` 區塊內。  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  設定 `DtrEnable` 屬性，指出電腦已準備好接受從數據機傳入的傳輸。  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  利用 <xref:System.IO.Ports.SerialPort.Write%2A> 方法，透過序列埠將撥接命令與電話號碼傳送至數據機。  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 此範例需要 <xref:System?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 此範例假設數據機已連接至 COM1。 建議您的程式碼允許使用者從可用序列埠清單中選取想要的序列埠。 如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。  
  
 此範例使用 `Using` 區塊以確保應用程式即使擲回例外狀況，也可關閉序列埠。 如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
 在此範例中，應用程式會在撥接數據機之後中斷與序列埠的連接。 實際上，您會想要將資料傳輸至數據機，或從中傳輸出。 如需詳細資訊，請參閱[如何：接收來自序列埠的字串](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [如何：將字串傳送至序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [如何：接收來自序列埠的字串](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
