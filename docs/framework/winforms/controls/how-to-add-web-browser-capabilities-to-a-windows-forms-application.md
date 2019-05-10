---
title: HOW TO：將網頁瀏覽器功能新增至 Windows Forms 應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: c091d9473bb7c3540453cb5763052f45f61b61f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624010"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="59a4f-102">HOW TO：將網頁瀏覽器功能新增至 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="59a4f-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="59a4f-103">利用 <xref:System.Windows.Forms.WebBrowser> 控制項，您可以將 Web 瀏覽器功能加入應用程式。</span><span class="sxs-lookup"><span data-stu-id="59a4f-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="59a4f-104">根據預設，此控制項的作用類似 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="59a4f-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="59a4f-105">設定 <xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性來載入初始 URL 之後，您可以按一下超連結或使用鍵盤快速鍵來巡覽，在巡覽歷程記錄中前後移動。</span><span class="sxs-lookup"><span data-stu-id="59a4f-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="59a4f-106">根據預設，您可以透過滑鼠右鍵捷徑功能表來存取其他瀏覽器功能。</span><span class="sxs-lookup"><span data-stu-id="59a4f-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="59a4f-107">您也可以將新文件拖曳至控制項加以開啟。</span><span class="sxs-lookup"><span data-stu-id="59a4f-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="59a4f-108"><xref:System.Windows.Forms.WebBrowser> 控制項也有數個屬性、方法和事件，可讓您用來實作類似 Internet Explorer 中的使用者介面功能。</span><span class="sxs-lookup"><span data-stu-id="59a4f-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="59a4f-109">下列程式碼範例會實作網址列、一般瀏覽器按鈕、[檔案] 功能表、狀態列，以及可顯示目前頁面標題的標題列。</span><span class="sxs-lookup"><span data-stu-id="59a4f-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59a4f-110">範例</span><span class="sxs-lookup"><span data-stu-id="59a4f-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59a4f-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="59a4f-111">Compiling the Code</span></span>  
 <span data-ttu-id="59a4f-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="59a4f-112">This example requires:</span></span>  
  
- <span data-ttu-id="59a4f-113">`System`、`System.Drawing` 和 `System.Windows.Forms` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="59a4f-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="59a4f-114">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="59a4f-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="59a4f-115">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="59a4f-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a4f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59a4f-116">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="59a4f-117">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="59a4f-117">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
