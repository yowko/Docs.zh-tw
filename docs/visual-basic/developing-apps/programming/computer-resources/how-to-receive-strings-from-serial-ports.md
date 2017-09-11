---
title: "如何：在 Visual Basic 中接收來自序列埠的字串"
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
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
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
ms.openlocfilehash: 500a6c651f6eb991eb9fefef601d0f593a38352f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="6c959-102">如何：在 Visual Basic 中接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="6c959-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="6c959-103">本主題描述如何在 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 中使用 `My.Computer.Ports` 來接收來自電腦序列埠的字串。</span><span class="sxs-lookup"><span data-stu-id="6c959-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="6c959-104">接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="6c959-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="6c959-105">將傳回字串初始化。</span><span class="sxs-lookup"><span data-stu-id="6c959-105">Initialize the return string.</span></span>  
  
     <span data-ttu-id="6c959-106">[!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-106">[!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]</span></span>  
  
2.  <span data-ttu-id="6c959-107">判斷會由哪個序列埠提供字串。</span><span class="sxs-lookup"><span data-stu-id="6c959-107">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="6c959-108">此範例假設會是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="6c959-108">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="6c959-109">請使用 `My.Computer.Ports.OpenSerialPort` 方法取得連接埠的參考。</span><span class="sxs-lookup"><span data-stu-id="6c959-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="6c959-110">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c959-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="6c959-111">`Try...Catch...Finally` 區塊允許應用程式即使產生例外狀況，也可關閉序列埠。</span><span class="sxs-lookup"><span data-stu-id="6c959-111">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="6c959-112">所有管理序列埠的程式碼都應該出現在此區塊內。</span><span class="sxs-lookup"><span data-stu-id="6c959-112">All code that manipulates the serial port should appear within this block.</span></span>  
  
     <span data-ttu-id="6c959-113">[!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-113">[!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]</span></span>  
  
4.  <span data-ttu-id="6c959-114">建立 `Do` 迴圈以讀取多行文字，直到再也沒有可用的文字行為止。</span><span class="sxs-lookup"><span data-stu-id="6c959-114">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     <span data-ttu-id="6c959-115">[!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-115">[!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]</span></span>  
  
5.  <span data-ttu-id="6c959-116">使用 <xref:System.IO.Ports.SerialPort.ReadLine%2A> 方法來讀取來自序列埠的下一行可用文字。</span><span class="sxs-lookup"><span data-stu-id="6c959-116">Use the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method to read the next available line of text from the serial port.</span></span>  
  
     <span data-ttu-id="6c959-117">[!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-117">[!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]</span></span>  
  
6.  <span data-ttu-id="6c959-118">使用 `If` 陳述式來判斷 <xref:System.IO.Ports.SerialPort.ReadLine%2A> 方法是否會傳回 `Nothing` (表示再也沒有可用的文字)。</span><span class="sxs-lookup"><span data-stu-id="6c959-118">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="6c959-119">如果它確實傳回 `Nothing`，請結束 `Do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="6c959-119">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     <span data-ttu-id="6c959-120">[!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-120">[!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]</span></span>  
  
7.  <span data-ttu-id="6c959-121">將 `Else` 區塊新增至 `If` 陳述式，以便處理實際讀取到字串的情況。</span><span class="sxs-lookup"><span data-stu-id="6c959-121">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="6c959-122">此區塊會將來自序列埠的字串附加至傳回字串。</span><span class="sxs-lookup"><span data-stu-id="6c959-122">The block appends the string from the serial port to the return string.</span></span>  
  
     <span data-ttu-id="6c959-123">[!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-123">[!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]</span></span>  
  
8.  <span data-ttu-id="6c959-124">傳回字串。</span><span class="sxs-lookup"><span data-stu-id="6c959-124">Return the string.</span></span>  
  
     <span data-ttu-id="6c959-125">[!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-125">[!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c959-126">範例</span><span class="sxs-lookup"><span data-stu-id="6c959-126">Example</span></span>  
 <span data-ttu-id="6c959-127">[!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="6c959-127">[!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]</span></span>  
  
 <span data-ttu-id="6c959-128">這個程式碼範例也可作為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="6c959-128">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6c959-129">在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。</span><span class="sxs-lookup"><span data-stu-id="6c959-129">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="6c959-130">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="6c959-130">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c959-131">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6c959-131">Compiling the Code</span></span>  
 <span data-ttu-id="6c959-132">此範例假設電腦使用的是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="6c959-132">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6c959-133">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6c959-133">Robust Programming</span></span>  
 <span data-ttu-id="6c959-134">此範例假設電腦使用的是 `COM1`。</span><span class="sxs-lookup"><span data-stu-id="6c959-134">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="6c959-135">為了具有更大的彈性，程式碼應該允許使用者從可用序列埠清單中選取想要的序列埠。</span><span class="sxs-lookup"><span data-stu-id="6c959-135">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="6c959-136">如需詳細資訊，請參閱[如何：顯示可用的序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="6c959-136">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="6c959-137">此範例使用 `Try...Catch...Finally` 區塊以確保應用程式會關閉序列埠，並攔截任何逾時例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6c959-137">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="6c959-138">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6c959-138">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c959-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c959-139">See Also</span></span>  
 <span data-ttu-id="6c959-140"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="6c959-140"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="6c959-141"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6c959-141"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="6c959-142">[如何：撥接與序列埠連接的數據機](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="6c959-142">[How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span></span>  
 <span data-ttu-id="6c959-143">[如何：將字串傳送至序列埠](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="6c959-143">[How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span></span>  
 [<span data-ttu-id="6c959-144">如何：顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="6c959-144">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

