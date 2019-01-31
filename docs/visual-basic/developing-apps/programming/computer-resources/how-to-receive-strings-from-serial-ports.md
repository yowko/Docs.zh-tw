---
title: HOW TO：在 Visual Basic 中接收來自序列埠的字串
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: f87ff7e621d241a94dae444bc156502ee86b36b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521604"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="56a48-102">HOW TO：在 Visual Basic 中接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="56a48-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="56a48-103">本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 來接收來自電腦序列埠的字串。</span><span class="sxs-lookup"><span data-stu-id="56a48-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="56a48-104">接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="56a48-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="56a48-105">將傳回字串初始化。</span><span class="sxs-lookup"><span data-stu-id="56a48-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  <span data-ttu-id="56a48-106">判斷會由哪個序列埠提供字串。</span><span class="sxs-lookup"><span data-stu-id="56a48-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="56a48-107">此範例假設會是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="56a48-107">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="56a48-108">請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。</span><span class="sxs-lookup"><span data-stu-id="56a48-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="56a48-109">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="56a48-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="56a48-110">`Try...Catch...Finally` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="56a48-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="56a48-111">所有管理序列埠的程式碼都應該出現在此區塊內。</span><span class="sxs-lookup"><span data-stu-id="56a48-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="56a48-112">建立 `Do` 迴圈以讀取多行文字，直到再也沒有可用的文字行為止。</span><span class="sxs-lookup"><span data-stu-id="56a48-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  <span data-ttu-id="56a48-113">使用 <xref:System.IO.Ports.SerialPort.ReadLine> 方法來讀取來自序列埠的下一行可用文字。</span><span class="sxs-lookup"><span data-stu-id="56a48-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  <span data-ttu-id="56a48-114">使用 `If` 陳述式來判斷 <xref:System.IO.Ports.SerialPort.ReadLine> 方法是否會傳回 `Nothing` (表示再也沒有可用的文字)。</span><span class="sxs-lookup"><span data-stu-id="56a48-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="56a48-115">如果它確實傳回 `Nothing`，請結束 `Do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="56a48-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  <span data-ttu-id="56a48-116">將 `Else` 區塊新增至 `If` 陳述式，以便處理實際讀取到字串的情況。</span><span class="sxs-lookup"><span data-stu-id="56a48-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="56a48-117">此區塊會將來自序列埠的字串附加至傳回字串。</span><span class="sxs-lookup"><span data-stu-id="56a48-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  <span data-ttu-id="56a48-118">傳回字串。</span><span class="sxs-lookup"><span data-stu-id="56a48-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="56a48-119">範例</span><span class="sxs-lookup"><span data-stu-id="56a48-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 <span data-ttu-id="56a48-120">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="56a48-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="56a48-121">在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。</span><span class="sxs-lookup"><span data-stu-id="56a48-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="56a48-122">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="56a48-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56a48-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="56a48-123">Compiling the Code</span></span>  
 <span data-ttu-id="56a48-124">此範例假設電腦使用的是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="56a48-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="56a48-125">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="56a48-125">Robust Programming</span></span>  
 <span data-ttu-id="56a48-126">此範例假設電腦使用的是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="56a48-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="56a48-127">為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。</span><span class="sxs-lookup"><span data-stu-id="56a48-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="56a48-128">如需詳細資訊，請參閱[＜How to：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="56a48-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="56a48-129">此範例使用 `Try...Catch...Finally` 區塊以確保應用程式會關閉序列埠，並攔截任何逾時例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56a48-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="56a48-130">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="56a48-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a48-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56a48-131">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="56a48-132">如何：撥接與序列埠連接的數據機</span><span class="sxs-lookup"><span data-stu-id="56a48-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="56a48-133">如何：將字串傳送至序列埠</span><span class="sxs-lookup"><span data-stu-id="56a48-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="56a48-134">如何：顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="56a48-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
