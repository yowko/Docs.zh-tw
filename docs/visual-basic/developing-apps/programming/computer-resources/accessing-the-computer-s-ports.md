---
title: "存取電腦的連接埠 (Visual Basic)"
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
- serial ports
- My.Computer.Ports object, tasks
ms.assetid: b04a2f76-992a-4585-ab41-8bbbdbd554a1
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: db4fdbea07000ab92d5329f53d68c61db9d0547d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="accessing-the-computer39s-ports-visual-basic"></a><span data-ttu-id="1c496-102">存取電腦的連接埠 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c496-102">Accessing the Computer&#39;s Ports (Visual Basic)</span></span>
<span data-ttu-id="1c496-103">`My.Computer.Ports` 物件提供屬性和方法來存取電腦的序列連接埠。</span><span class="sxs-lookup"><span data-stu-id="1c496-103">The `My.Computer.Ports` object provides a property and a method for accessing the computer's serial ports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c496-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1c496-104">In This Section</span></span>  
 [<span data-ttu-id="1c496-105">如何：顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="1c496-105">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)  
 <span data-ttu-id="1c496-106">示範如何顯示可用的序列埠。</span><span class="sxs-lookup"><span data-stu-id="1c496-106">Demonstrates how to show available serial ports.</span></span>  
  
 [<span data-ttu-id="1c496-107">如何：撥接與序列埠連接的數據機</span><span class="sxs-lookup"><span data-stu-id="1c496-107">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 <span data-ttu-id="1c496-108">示範如何撥接連接到電腦序列埠的數據機。</span><span class="sxs-lookup"><span data-stu-id="1c496-108">Demonstrates how to dial a modem attached to the serial port of a computer.</span></span>  
  
 [<span data-ttu-id="1c496-109">如何：將字串傳送至序列埠</span><span class="sxs-lookup"><span data-stu-id="1c496-109">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 <span data-ttu-id="1c496-110">示範如何將字串傳送至電腦的序列埠。</span><span class="sxs-lookup"><span data-stu-id="1c496-110">Demonstrates how to send a string to a computer's serial port.</span></span>  
  
 [<span data-ttu-id="1c496-111">如何：接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="1c496-111">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 <span data-ttu-id="1c496-112">示範如何接收來自電腦序列埠的字串。</span><span class="sxs-lookup"><span data-stu-id="1c496-112">Demonstrates how to receive a string from a computer's serial port.</span></span>  
  
 [<span data-ttu-id="1c496-113">.NET Framework 中的連接埠作業</span><span class="sxs-lookup"><span data-stu-id="1c496-113">Port Operations in the .NET Framework</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/port-operations-in-the-net-framework.md)  
 <span data-ttu-id="1c496-114">描述如何在執行連接埠作業時使用 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1c496-114">Describes how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] when performing port operations.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c496-115">參考資料</span><span class="sxs-lookup"><span data-stu-id="1c496-115">Reference</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <span data-ttu-id="1c496-116">描述 `My.Computer.Ports` 物件和其成員。</span><span class="sxs-lookup"><span data-stu-id="1c496-116">Describes the `My.Computer.Ports` object and its members.</span></span>  
  
 <xref:Microsoft.VisualBasic.Devices.Ports.SerialPortNames%2A>  
 <span data-ttu-id="1c496-117">描述 `SerialPortNames` 屬性，取得電腦上序列埠名稱的集合。</span><span class="sxs-lookup"><span data-stu-id="1c496-117">Describes the `SerialPortNames` property, which gets a collection of the names of the serial ports on the computer.</span></span>  
  
 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>  
 <span data-ttu-id="1c496-118">描述 `OpenSerialPort` 方法，此方法會建立並開啟 <xref:System.IO.Ports.SerialPort?displayProperty=fullName> 物件。</span><span class="sxs-lookup"><span data-stu-id="1c496-118">Describes the `OpenSerialPort` method, which creates and opens a <xref:System.IO.Ports.SerialPort?displayProperty=fullName> object.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1c496-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="1c496-119">Related Sections</span></span>  
 <xref:System.IO.Ports.SerialPort>  
 <span data-ttu-id="1c496-120">描述 .NET Framework <xref:System.IO.Ports.SerialPort> 類別。</span><span class="sxs-lookup"><span data-stu-id="1c496-120">Describes the .NET Framework <xref:System.IO.Ports.SerialPort> class.</span></span>

