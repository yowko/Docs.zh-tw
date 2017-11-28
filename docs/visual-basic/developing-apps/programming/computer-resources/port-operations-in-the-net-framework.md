---
title: ".NET Framework 中使用 Visual Basic 的連接埠作業"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8db016461ea204eaf349a2c588670a237c9e583b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>.NET Framework 中使用 Visual Basic 的連接埠作業
您可以透過 <xref:System.IO.Ports?displayProperty=nameWithType> 命名空間中的 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 類別，以存取電腦的序列埠。 做為最重要的類別，<xref:System.IO.Ports.SerialPort> 會提供同步化與事件驅動之 I/O 的架構、PIN 和中斷狀態的存取權，以及序列驅動程式屬性的存取權。 它可以包裝在 <xref:System.IO.Stream> 物件中，該物件可透過 <xref:System.IO.Ports.SerialPort.BaseStream%2A> 屬性存取。 將 <xref:System.IO.Ports.SerialPort> 包裝在 <xref:System.IO.Stream> 物件中，可讓使用資料流的類別存取序列埠。 命名空間包含可簡化序列埠控制的列舉。  
  
 建立 <xref:System.IO.Ports.SerialPort> 物件最簡單的方式，是透過 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> 方法。  
  
> [!NOTE]
>  您不能使用 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 類別直接存取其他連接埠型別，例如平行連接埠、USB 埠等等。  
  
## <a name="enumerations"></a>列舉  
 本表會列出並說明用於存取序列埠的主要列舉︰  
  
|列舉|說明|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|指定建立 <xref:System.IO.Ports.SerialPort> 物件之序列埠通訊使用的控制通訊協定。|  
|<xref:System.IO.Ports.Parity>|指定 <xref:System.IO.Ports.SerialPort> 物件的同位位元。|  
|<xref:System.IO.Ports.SerialData>|指定 <xref:System.IO.Ports.SerialPort> 物件之序列埠接收到的字元類型。|  
|<xref:System.IO.Ports.SerialError>|指定在 <xref:System.IO.Ports.SerialPort> 物件上發生的錯誤|  
|<xref:System.IO.Ports.SerialPinChange>|指定在 <xref:System.IO.Ports.SerialPort> 物件上發生的變更類型。|  
|<xref:System.IO.Ports.StopBits>|指定在 <xref:System.IO.Ports.SerialPort> 物件上使用的停止位元數目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [存取電腦的連接埠](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
