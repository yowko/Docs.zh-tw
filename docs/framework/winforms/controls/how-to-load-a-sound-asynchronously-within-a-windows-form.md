---
title: 如何：在 Windows Form 中非同步地載入音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 9ebede03a3a9d2cc6db1cda2537bcaf30afcb2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533565"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="b303f-102">如何：在 Windows Form 中非同步地載入音效</span><span class="sxs-lookup"><span data-stu-id="b303f-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="b303f-103">下列程式碼範例會以非同步方式從 URL 載入音效，然後在新的執行緒上播放。</span><span class="sxs-lookup"><span data-stu-id="b303f-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b303f-104">範例</span><span class="sxs-lookup"><span data-stu-id="b303f-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b303f-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b303f-105">Compiling the Code</span></span>  
 <span data-ttu-id="b303f-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b303f-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b303f-107">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b303f-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="b303f-108">您將檔案名稱 `"http://www.tailspintoys.com/sounds/stop.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b303f-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="b303f-109">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b303f-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b303f-110">您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。</span><span class="sxs-lookup"><span data-stu-id="b303f-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b303f-111">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="b303f-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b303f-112">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="b303f-112">Robust Programming</span></span>  
 <span data-ttu-id="b303f-113">檔案作業應含括在適當的例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="b303f-113">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="b303f-114">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b303f-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b303f-115">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="b303f-115">The path name is malformed.</span></span> <span data-ttu-id="b303f-116">例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b303f-116">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="b303f-117">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b303f-117">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="b303f-118">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b303f-118">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="b303f-119">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b303f-119">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="b303f-120">此路徑無效 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b303f-120">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="b303f-121">路徑只有一個冒號 ":" (<xref:System.NotSupportedException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b303f-121">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b303f-122">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b303f-122">.NET Framework Security</span></span>  
 <span data-ttu-id="b303f-123">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="b303f-123">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b303f-124">例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="b303f-124">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="b303f-125">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="b303f-125">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b303f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b303f-126">See Also</span></span>  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [<span data-ttu-id="b303f-127">操作說明：播放 Windows Forms 中的音效</span><span class="sxs-lookup"><span data-stu-id="b303f-127">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
