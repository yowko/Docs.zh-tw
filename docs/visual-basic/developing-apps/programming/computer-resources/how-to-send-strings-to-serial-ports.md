---
title: 作法：在 Visual Basic 中將字串傳送至序列埠
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66f7d0b51e51f6d550a42cca55b3194c2e273969
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662732"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="a90e9-102">作法：在 Visual Basic 中將字串傳送至序列埠</span><span class="sxs-lookup"><span data-stu-id="a90e9-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="a90e9-103">本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 將字串傳送至電腦的序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a90e9-104">範例</span><span class="sxs-lookup"><span data-stu-id="a90e9-104">Example</span></span>  
 <span data-ttu-id="a90e9-105">此範例會將字串傳送至 COM1 序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="a90e9-106">您可能需要使用電腦上不同的序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="a90e9-107">請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。</span><span class="sxs-lookup"><span data-stu-id="a90e9-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a90e9-108">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="a90e9-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="a90e9-109">`Using` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a90e9-110">所有管理序列埠的程式碼都應該出現在此區塊或 `Try...Catch...Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="a90e9-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="a90e9-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> 方法會將資料傳送至序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a90e9-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a90e9-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="a90e9-113">此範例假設電腦使用的是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="a90e9-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a90e9-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="a90e9-114">Robust Programming</span></span>  
 <span data-ttu-id="a90e9-115">此範例假設電腦使用的是 `COM1`；為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a90e9-116">如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="a90e9-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a90e9-117">此範例使用 `Using` 區塊以確保應用程式即使擲回例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="a90e9-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="a90e9-118">如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a90e9-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90e9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a90e9-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a90e9-120">如何：撥接與序列埠連接的數據機</span><span class="sxs-lookup"><span data-stu-id="a90e9-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="a90e9-121">如何：顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="a90e9-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
