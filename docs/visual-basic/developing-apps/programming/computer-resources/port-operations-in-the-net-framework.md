---
title: ".NET Framework 中使用 Visual Basic 的連接埠作業 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 61b91fe5f3bb016bace838b9eeabb1a59190bfe9
ms.lasthandoff: 03/13/2017

---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>.NET Framework 中使用 Visual Basic 的連接埠作業
您可以透過 <xref:System.IO.Ports?displayProperty=fullName> 命名空間中的 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 類別存取電腦的序列埠。 最重要的類別 <xref:System.IO.Ports.SerialPort> 會提供同步化與事件驅動之 I/O 的架構、Pin 和中斷狀態的存取權，以及序列驅動程式屬性的存取權。 它可以包裝在 <xref:System.IO.Stream> 物件中，透過 <xref:System.IO.Ports.SerialPort.BaseStream%2A> 屬性存取。 以 <xref:System.IO.Stream> 物件包裝 <xref:System.IO.Ports.SerialPort> 可讓使用資料流的類別存取序列埠。 命名空間包含可簡化序列埠控制的列舉。  
  
 透過 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> 方法建立 <xref:System.IO.Ports.SerialPort> 物件是最簡單的方式。  
  
> [!NOTE]
>  您不能使用 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 類別直接存取其他連接埠型別，例如平行連接埠、USB 埠等等。  
  
## <a name="enumerations"></a>列舉  
 本表會列出並說明用於存取序列埠的主要列舉︰  
  
|列舉|描述|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|指定建立 <xref:System.IO.Ports.SerialPort> 物件序列埠通訊所使用的控制通訊協定。|  
|<xref:System.IO.Ports.Parity>|指定 <xref:System.IO.Ports.SerialPort> 物件的同位位元。|  
|<xref:System.IO.Ports.SerialData>|指定 <xref:System.IO.Ports.SerialPort> 物件序列埠接收到的字元型別。|  
|<xref:System.IO.Ports.SerialError>|指定 <xref:System.IO.Ports.SerialPort> 物件上發生的錯誤|  
|<xref:System.IO.Ports.SerialPinChange>|指定 <xref:System.IO.Ports.SerialPort> 物件上發生的變更型別。|  
|<xref:System.IO.Ports.StopBits>|指定 <xref:System.IO.Ports.SerialPort> 物件上使用的停止位元數。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [存取電腦的連接埠](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
