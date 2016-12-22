---
title: "How to: Show Available Serial Ports in Visual Basic | Microsoft Docs"
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
  - "serial ports, availability"
  - "My.Computer.Ports.SerialPortNames property"
  - "My.Computer.Ports object"
  - "ports, serial port availability"
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Show Available Serial Ports in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

此主題會描述如何使用 `My.Computer.Ports`，顯示 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中可用的電腦序列埠。  
  
 為了讓使用者能夠選取要使用的連接埠，序列埠的名稱會放置在 <xref:System.Windows.Forms.ListBox> 控制項中。  
  
## 範例  
 這個範例會對 `My.Computer.Ports.SerialPortNames` 屬性 \(Property\) 傳回的所有字串 \(String\) 執行迴圈 \(Loop\)。  這些字串都是電腦上可用序列埠的名稱。  
  
 一般而言，使用者會從可用的連接埠清單中，選取應用程式應該使用的序列埠。  在這個範例中，序列埠名稱會儲存在 <xref:System.Windows.Forms.ListBox> 控制項中。  如需詳細資訊，請參閱 [ListBox 控制項](../Topic/ListBox%20Control%20\(Windows%20Forms\).md)。  
  
 [!CODE [VbVbalrMyComputer#45](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyComputer#45)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**連線和網路**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   參考 System.Windows.Forms.dll 的專案。  
  
-   對 <xref:System.Windows.Forms> 命名空間成員的存取權。  如果您的程式碼中未完整限定成員名稱，請加入 `Imports` 陳述式。  如需詳細資訊，請參閱 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
-   您的表單具有名為 `ListBox1` 的 <xref:System.Windows.Forms.ListBox> 控制項。  
  
## 穩固程式設計  
 您不一定要使用 <xref:System.Windows.Forms.ListBox> 控制項，也能顯示可用的序列埠名稱。  也可以改用 <xref:System.Windows.Forms.ComboBox> 或其他控制項。  如果應用程式不需要使用者的回應，您還可以使用 <xref:System.Windows.Forms.TextBox> 控制項顯示資訊。  
  
> [!NOTE]
>  在 Windows 98 上執行時，`My.Computer.Ports.SerialPortNames` 所傳回的連接埠名稱可能是不正確的。  若要避免應用程式的錯誤，請在使用這些連接埠名稱開啟連接埠時，使用例外狀況處理，例如，`Try...Catch...Finally` 陳述式或 `Using` 陳述式。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [How to: Dial Modems Attached to Serial Ports](../Topic/How%20to:%20Dial%20Modems%20Attached%20to%20Serial%20Ports%20in%20Visual%20Basic.md)   
 [How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)