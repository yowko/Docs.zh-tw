---
title: 作法：在 Visual Basic 中撥接與序列埠連接的數據機
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db482af7750012d8805d4f834063a2c82224cf67
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337028"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="00106-102">作法：在 Visual Basic 中撥接與序列埠連接的數據機</span><span class="sxs-lookup"><span data-stu-id="00106-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="00106-103">本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 撥接數據機。</span><span class="sxs-lookup"><span data-stu-id="00106-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="00106-104">一般而言，數據機會連接至電腦上的其中一個序列埠。</span><span class="sxs-lookup"><span data-stu-id="00106-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="00106-105">您的應用程式必須將命令傳送至適當的序列埠，才能與數據機通訊。</span><span class="sxs-lookup"><span data-stu-id="00106-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="00106-106">撥接數據機</span><span class="sxs-lookup"><span data-stu-id="00106-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="00106-107">判斷要將數據機連接至哪一個序列埠。</span><span class="sxs-lookup"><span data-stu-id="00106-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="00106-108">此範例假設數據機是在 COM1。</span><span class="sxs-lookup"><span data-stu-id="00106-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="00106-109">請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。</span><span class="sxs-lookup"><span data-stu-id="00106-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="00106-110">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="00106-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="00106-111">`Using` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="00106-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="00106-112">所有管理序列埠的程式碼都應該出現在此區塊或 `Try...Catch...Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="00106-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="00106-113">設定 `DtrEnable` 屬性，指出電腦已準備好接受從數據機傳入的傳輸。</span><span class="sxs-lookup"><span data-stu-id="00106-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="00106-114">利用 <xref:System.IO.Ports.SerialPort.Write%2A> 方法，透過序列埠將撥接命令與電話號碼傳送至數據機。</span><span class="sxs-lookup"><span data-stu-id="00106-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="00106-115">範例</span><span class="sxs-lookup"><span data-stu-id="00106-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="00106-116">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="00106-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="00106-117">在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。</span><span class="sxs-lookup"><span data-stu-id="00106-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="00106-118">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="00106-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00106-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="00106-119">Compiling the Code</span></span>  
 <span data-ttu-id="00106-120">此範例需要 <xref:System?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="00106-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="00106-121">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="00106-121">Robust Programming</span></span>  
 <span data-ttu-id="00106-122">此範例假設數據機已連接至 COM1。</span><span class="sxs-lookup"><span data-stu-id="00106-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="00106-123">建議您的程式碼允許使用者從可用序列埠清單中選取想要的序列埠。</span><span class="sxs-lookup"><span data-stu-id="00106-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="00106-124">如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="00106-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="00106-125">此範例使用 `Using` 區塊以確保應用程式即使擲回例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="00106-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="00106-126">如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="00106-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="00106-127">在此範例中，應用程式會在撥接數據機之後中斷與序列埠的連接。</span><span class="sxs-lookup"><span data-stu-id="00106-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="00106-128">實際上，您會想要將資料傳輸至數據機，或從中傳輸出。</span><span class="sxs-lookup"><span data-stu-id="00106-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="00106-129">如需詳細資訊，請參閱[如何：接收來自序列埠的字串](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="00106-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00106-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00106-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="00106-131">作法：將字串傳送至序列埠</span><span class="sxs-lookup"><span data-stu-id="00106-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="00106-132">作法：接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="00106-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="00106-133">作法：顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="00106-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
