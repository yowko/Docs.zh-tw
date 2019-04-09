---
title: HOW TO：在 Windows Forms 中以非同步方式載入音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 1d710f1e6d3b208365d5b1eb2524fbeeaa673c2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185753"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="14bb6-102">HOW TO：在 Windows Forms 中以非同步方式載入音效</span><span class="sxs-lookup"><span data-stu-id="14bb6-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="14bb6-103">下列程式碼範例會以非同步方式從 URL 載入音效，然後在新的執行緒上播放。</span><span class="sxs-lookup"><span data-stu-id="14bb6-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14bb6-104">範例</span><span class="sxs-lookup"><span data-stu-id="14bb6-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14bb6-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="14bb6-105">Compiling the Code</span></span>  
 <span data-ttu-id="14bb6-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="14bb6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="14bb6-107">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="14bb6-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="14bb6-108">您將檔案名稱 `"http://www.tailspintoys.com/sounds/stop.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="14bb6-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="14bb6-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="14bb6-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="14bb6-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="14bb6-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="14bb6-111">Robust Programming</span></span>  
 <span data-ttu-id="14bb6-112">檔案作業應含括在適當的例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="14bb6-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="14bb6-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="14bb6-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="14bb6-114">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="14bb6-114">The path name is malformed.</span></span> <span data-ttu-id="14bb6-115">例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-115">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="14bb6-116">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="14bb6-117">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="14bb6-118">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="14bb6-119">此路徑無效 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-119">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="14bb6-120">此路徑只是一個冒號 ":" (<xref:System.NotSupportedException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="14bb6-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="14bb6-121">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="14bb6-121">.NET Framework Security</span></span>  
 <span data-ttu-id="14bb6-122">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="14bb6-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="14bb6-123">例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="14bb6-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="14bb6-124">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="14bb6-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bb6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14bb6-125">See also</span></span>

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="14bb6-126">HOW TO：播放 Windows Forms 的音效</span><span class="sxs-lookup"><span data-stu-id="14bb6-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
