---
title: "How to: Dial Modems Attached to Serial Ports in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "modems, dialing"
  - "serial ports, dialing"
  - "My.Computer.Ports object"
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Dial Modems Attached to Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

此主題將說明如何使用 `My.Computer.Ports` 在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中撥接數據機。  
  
 一般而言，數據機會連接至電腦上的其中一個序列埠。  若要讓您的應用程式與數據機通訊，它必須傳送命令給適當的序列埠。  
  
### 若要撥接數據機  
  
1.  判斷要將數據機連接至哪一個序列埠。  此範例會假設數據機是在 COM1。  
  
2.  請使用 `My.Computer.Ports.OpenSerialPort` 方法取得對連接埠的參考。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。  
  
     即使發生例外狀況，`Using` 區塊也會允許應用程式關閉序列埠。  所有控制序列埠的程式碼應該都會顯示在這個區塊中，或是在 `Try...Catch...Finally` 區塊內。  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#28)]  
  
3.  設定 `DtrEnable` 屬性，指出電腦已準備好，可以接受從數據機收到的傳送。  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#29)]  
  
4.  利用 <xref:System.IO.Ports.SerialPort.Write%2A> 方法，透過序列埠，將撥接命令與電話號碼傳送到數據機。  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#30)]  
  
## 範例  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/VbVbalrMyComputer/Class2.vb#27)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**連線和網路**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
## 編譯程式碼  
 這個範例需要有 <xref:System?displayProperty=fullName> 命名空間的參考。  
  
## 穩固程式設計  
 此範例會假設數據機是連接至 COM1。  建議您的程式碼允許使用者從可用埠清單中選取想要的序列埠。  如需詳細資訊，請參閱 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。  
  
 這個範例使用 `Using` 區塊，確定應用程式即使擲回例外狀況，也會關閉連接埠。  如需詳細資訊，請參閱 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
 在此範例中，應用程式會在撥接數據機之後，中斷它與序列埠的連接。  實際上，您會想要將資料傳送至數據機，以及從數據機傳送資料。  如需詳細資訊，請參閱 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)