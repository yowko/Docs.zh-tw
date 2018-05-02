---
title: 如何：在 Visual Basic 中將字串傳送至序列埠
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d796f2d581188fd3753bf3d18b04b2fbeb901945
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="09bcb-102">如何：在 Visual Basic 中將字串傳送至序列埠</span><span class="sxs-lookup"><span data-stu-id="09bcb-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="09bcb-103">本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 將字串傳送至電腦的序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09bcb-104">範例</span><span class="sxs-lookup"><span data-stu-id="09bcb-104">Example</span></span>  
 <span data-ttu-id="09bcb-105">此範例會將字串傳送至 COM1 序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="09bcb-106">您可能需要使用電腦上不同的序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="09bcb-107">請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。</span><span class="sxs-lookup"><span data-stu-id="09bcb-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="09bcb-108">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="09bcb-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="09bcb-109">`Using` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="09bcb-110">所有管理序列埠的程式碼都應該出現在此區塊或 `Try...Catch...Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="09bcb-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="09bcb-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> 方法會將資料傳送至序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09bcb-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="09bcb-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="09bcb-113">此範例假設電腦使用的是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="09bcb-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="09bcb-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="09bcb-114">Robust Programming</span></span>  
 <span data-ttu-id="09bcb-115">此範例假設電腦使用的是 `COM1`；為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="09bcb-116">如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="09bcb-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="09bcb-117">此範例使用 `Using` 區塊以確保應用程式即使擲回例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="09bcb-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="09bcb-118">如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="09bcb-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09bcb-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="09bcb-119">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="09bcb-120">如何：撥接與序列埠連接的數據機</span><span class="sxs-lookup"><span data-stu-id="09bcb-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="09bcb-121">如何：顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="09bcb-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
