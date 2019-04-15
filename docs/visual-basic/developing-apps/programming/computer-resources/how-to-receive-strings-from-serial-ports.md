---
title: 作法：在 Visual Basic 中接收來自序列埠的字串
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 6c832cd9ef5df904850261f4de2d769bfc28c3cb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296715"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>作法：在 Visual Basic 中接收來自序列埠的字串
本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 來接收來自電腦序列埠的字串。  
  
### <a name="to-receive-strings-from-the-serial-port"></a>接收來自序列埠的字串  
  
1. 將傳回字串初始化。  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. 判斷會由哪個序列埠提供字串。 此範例假設會是 `COM1`。  
  
3. 請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。  
  
     `Try...Catch...Finally` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。 所有管理序列埠的程式碼都應該出現在此區塊內。  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. 建立 `Do` 迴圈以讀取多行文字，直到再也沒有可用的文字行為止。  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. 使用 <xref:System.IO.Ports.SerialPort.ReadLine> 方法來讀取來自序列埠的下一行可用文字。  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. 使用 `If` 陳述式來判斷 <xref:System.IO.Ports.SerialPort.ReadLine> 方法是否會傳回 `Nothing` (表示再也沒有可用的文字)。 如果它確實傳回 `Nothing`，請結束 `Do` 迴圈。  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. 將 `Else` 區塊新增至 `If` 陳述式，以便處理實際讀取到字串的情況。 此區塊會將來自序列埠的字串附加至傳回字串。  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. 傳回字串。  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 此範例假設電腦使用的是 `COM1`。  
  
## <a name="robust-programming"></a>穩固程式設計  
 此範例假設電腦使用的是 `COM1`。 為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。 如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。  
  
 此範例使用 `Try...Catch...Finally` 區塊以確保應用程式會關閉序列埠，並攔截任何逾時例外狀況。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [作法：撥接與序列埠連接的數據機](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [作法：將字串傳送至序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [作法：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
