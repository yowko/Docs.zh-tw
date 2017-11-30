---
title: "如何：在 Windows Form 上循環播放音效"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e61a15a7a249a90ce9eca035ebe6fd67275bb74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="f5cda-102">如何：在 Windows Form 上循環播放音效</span><span class="sxs-lookup"><span data-stu-id="f5cda-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="f5cda-103">下列程式碼範例會重複播放音效。</span><span class="sxs-lookup"><span data-stu-id="f5cda-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="f5cda-104">當 `stopPlayingButton_Click` 事件處理常式中的程式碼執行時，會停止目前正在播放任何聲音。</span><span class="sxs-lookup"><span data-stu-id="f5cda-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="f5cda-105">如果未播放聲音，就不會發生任何事。</span><span class="sxs-lookup"><span data-stu-id="f5cda-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cda-106">範例</span><span class="sxs-lookup"><span data-stu-id="f5cda-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5cda-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f5cda-107">Compiling the Code</span></span>  
 <span data-ttu-id="f5cda-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f5cda-108">This example requires:</span></span>  
  
-   <span data-ttu-id="f5cda-109">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="f5cda-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="f5cda-110">您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f5cda-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="f5cda-111">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f5cda-112">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="f5cda-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f5cda-113">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="f5cda-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f5cda-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f5cda-114">Robust Programming</span></span>  
 <span data-ttu-id="f5cda-115">檔案作業應含括在適當的例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="f5cda-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="f5cda-116">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="f5cda-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f5cda-117">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="f5cda-117">The path name is malformed.</span></span> <span data-ttu-id="f5cda-118">例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="f5cda-119">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="f5cda-120">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="f5cda-121">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="f5cda-122">路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="f5cda-123">路徑只有一個冒號 ":" (<xref:System.NotSupportedException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f5cda-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f5cda-124">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="f5cda-124">.NET Framework Security</span></span>  
 <span data-ttu-id="f5cda-125">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="f5cda-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f5cda-126">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="f5cda-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="f5cda-127">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="f5cda-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cda-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5cda-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="f5cda-129">操作說明：播放 Windows Forms 中的音效</span><span class="sxs-lookup"><span data-stu-id="f5cda-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="f5cda-130">SoundPlayer 類別概觀</span><span class="sxs-lookup"><span data-stu-id="f5cda-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
