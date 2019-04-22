---
title: HOW TO：在 Visual Basic 中顯示可用的序列埠
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 57b3a33fecb6128a10ce903fd26724de98acb8c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834643"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="59c05-102">HOW TO：在 Visual Basic 中顯示可用的序列埠</span><span class="sxs-lookup"><span data-stu-id="59c05-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="59c05-103">本主題描述如何在 Visual Basic 中使用 `My.Computer.Ports` 來顯示電腦的可用序列埠。</span><span class="sxs-lookup"><span data-stu-id="59c05-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="59c05-104">為了允許使用者選取所要使用的序列埠，序列埠的名稱放在 <xref:System.Windows.Forms.ListBox> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="59c05-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59c05-105">範例</span><span class="sxs-lookup"><span data-stu-id="59c05-105">Example</span></span>  
 <span data-ttu-id="59c05-106">此範例會針對 `My.Computer.Ports.SerialPortNames` 屬性傳回的所有字串執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="59c05-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="59c05-107">這些字串是電腦上可用序列埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="59c05-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="59c05-108">一般而言，使用者會從可用的序列埠清單中，選取應用程式應該使用的序列埠。</span><span class="sxs-lookup"><span data-stu-id="59c05-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="59c05-109">在這個範例中，序列埠名稱會儲存在 <xref:System.Windows.Forms.ListBox> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="59c05-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="59c05-110">如需詳細資訊，請參閱 [ListBox 控制項](../../../../framework/winforms/controls/listbox-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="59c05-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="59c05-111">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="59c05-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="59c05-112">在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。</span><span class="sxs-lookup"><span data-stu-id="59c05-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="59c05-113">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="59c05-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59c05-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="59c05-114">Compiling the Code</span></span>  
 <span data-ttu-id="59c05-115">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="59c05-115">This example requires:</span></span>  
  
-   <span data-ttu-id="59c05-116">System.Windows.Forms.dll 的專案參考。</span><span class="sxs-lookup"><span data-stu-id="59c05-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="59c05-117"><xref:System.Windows.Forms> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="59c05-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="59c05-118">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="59c05-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="59c05-119">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="59c05-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="59c05-120">您的表單會有名為 `ListBox1` 的 <xref:System.Windows.Forms.ListBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="59c05-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="59c05-121">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="59c05-121">Robust Programming</span></span>  
 <span data-ttu-id="59c05-122">您不一定要使用 <xref:System.Windows.Forms.ListBox> 控制項來顯示可用的序列埠名稱。</span><span class="sxs-lookup"><span data-stu-id="59c05-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="59c05-123">相反地，您可以使用 <xref:System.Windows.Forms.ComboBox> 或其他控制項。</span><span class="sxs-lookup"><span data-stu-id="59c05-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="59c05-124">如果應用程式不需要使用者的回應，您還可以使用 <xref:System.Windows.Forms.TextBox> 控制項來顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="59c05-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59c05-125">在 Windows 98 上執行時，`My.Computer.Ports.SerialPortNames` 所傳回的序列埠名稱可能不正確。</span><span class="sxs-lookup"><span data-stu-id="59c05-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="59c05-126">為了避免應用程式錯誤，請在使用序列埠名稱開啟序列埠時，使用例外狀況處理，例如 `Try...Catch...Finally` 陳述式或 `Using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="59c05-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c05-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c05-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="59c05-128">如何：撥接與序列埠連接的數據機</span><span class="sxs-lookup"><span data-stu-id="59c05-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="59c05-129">如何：將字串傳送至序列埠</span><span class="sxs-lookup"><span data-stu-id="59c05-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="59c05-130">如何：接收來自序列埠的字串</span><span class="sxs-lookup"><span data-stu-id="59c05-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
