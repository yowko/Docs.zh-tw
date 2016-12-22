---
title: "How to: Send Strings to Serial Ports in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ports, sending strings to"
  - "strings [Visual Basic], sending to serial ports"
  - "My.Computer.Ports object"
  - "serial ports, sending strings to"
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Send Strings to Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

本主題將描述如何在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中使用 `My.Computer.Ports` 將字串傳送至電腦的序列埠。  
  
## 範例  
 這個範例會將字串傳送至 COM1 序列埠。  您可能需要使用電腦上不同的序列埠。  
  
 請使用 `My.Computer.Ports.OpenSerialPort` 方法取得對連接埠的參考。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。  
  
 即使發生例外狀況，`Using` 區塊也會允許應用程式關閉序列埠。  所有控制序列埠的程式碼都應該會顯示在這個區塊或 `Try...Catch...Finally` 區塊中。  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> 方法會將資料傳送至序列埠。  
  
 [!CODE [VbVbalrMyComputer#33](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyComputer#33)]  
  
## 編譯程式碼  
  
-   這個範例會假設電腦所使用的是 `COM1`。  
  
## 穩固程式設計  
 這個範例會假設電腦所使用的是 `COM1`。為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。  如需詳細資訊，請參閱 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。  
  
 這個範例使用 `Using` 區塊，確定應用程式即使擲回例外狀況，也會關閉連接埠。  如需詳細資訊，請參閱 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [How to: Dial Modems Attached to Serial Ports](../Topic/How%20to:%20Dial%20Modems%20Attached%20to%20Serial%20Ports%20in%20Visual%20Basic.md)   
 [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)