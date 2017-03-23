---
title: "Port Operations in the .NET Framework with Visual Basic | Microsoft Docs"
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
  - "ports, Visual Basic"
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Port Operations in the .NET Framework with Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以透過 <xref:System.IO.Ports?displayProperty=fullName> 命名空間中的 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別，存取電腦的序列埠。  最重要的類別 \(Class\) <xref:System.IO.Ports.SerialPort> 會提供同步化與事件驅動之 I\/O 的架構、Pin 和中斷狀態的存取權，以及序列驅動程式屬性的存取權。  可以在 <xref:System.IO.Stream> 物件中包裝它，並且可以透過 <xref:System.IO.Ports.SerialPort.BaseStream%2A> 屬性存取它。  在 <xref:System.IO.Stream> 物件中包裝 <xref:System.IO.Ports.SerialPort>，即可讓使用資料流的類別存取序列埠。  命名空間包含簡化序列埠之控制的列舉型別 \(Enumeration\)。  
  
 建立 <xref:System.IO.Ports.SerialPort> 物件的最簡單方式就是透過 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> 方法。  
  
> [!NOTE]
>  您不能直接使用 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別存取其他類型的埠 \(例如，平行埠、USB 埠等等\)。  
  
## 列舉  
 此表會列出並描述用於存取序列埠的主要列舉型別：  
  
|||  
|-|-|  
|列舉|描述|  
|<xref:System.IO.Ports.Handshake>|指定在建立 <xref:System.IO.Ports.SerialPort> 物件的序列埠通訊時使用的傳輸通訊協定。|  
|<xref:System.IO.Ports.Parity>|指定 <xref:System.IO.Ports.SerialPort> 物件的同位檢查位元。|  
|<xref:System.IO.Ports.SerialData>|指定在 <xref:System.IO.Ports.SerialPort> 物件之序列埠上收到的字元型別。|  
|<xref:System.IO.Ports.SerialError>|指定在 <xref:System.IO.Ports.SerialPort> 物件上發生的錯誤。|  
|<xref:System.IO.Ports.SerialPinChange>|指定在 <xref:System.IO.Ports.SerialPort> 物件上發生的變更型別。|  
|<xref:System.IO.Ports.StopBits>|指定在 <xref:System.IO.Ports.SerialPort> 物件上所使用的停止位元數。|  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)