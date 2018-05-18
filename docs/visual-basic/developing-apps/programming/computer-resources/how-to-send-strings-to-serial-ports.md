---
title: 如何：在 Visual Basic 中將字串傳送至序列埠
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: a00306407cfe880ebc915d74a753109cc9696f6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>如何：在 Visual Basic 中將字串傳送至序列埠
本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 將字串傳送至電腦的序列埠。  
  
## <a name="example"></a>範例  
 此範例會將字串傳送至 COM1 序列埠。 您可能需要使用電腦上不同的序列埠。  
  
 請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。  
  
 `Using` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。 所有管理序列埠的程式碼都應該出現在此區塊或 `Try...Catch...Finally` 區塊內。  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> 方法會將資料傳送至序列埠。  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   此範例假設電腦使用的是 `COM1`。  
  
## <a name="robust-programming"></a>穩固程式設計  
 此範例假設電腦使用的是 `COM1`；為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。 如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。  
  
 此範例使用 `Using` 區塊以確保應用程式即使擲回例外狀況，也可關閉序列埠。 如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [如何：撥接與序列埠連接的數據機](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
