---
title: 作法：循環播放 Windows Forms 的音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592354"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="18283-102">作法：循環播放 Windows Forms 的音效</span><span class="sxs-lookup"><span data-stu-id="18283-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="18283-103">下列程式碼範例會重複播放音效。</span><span class="sxs-lookup"><span data-stu-id="18283-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="18283-104">當 `stopPlayingButton_Click` 事件處理常式中的程式碼執行時，會停止目前正在播放任何聲音。</span><span class="sxs-lookup"><span data-stu-id="18283-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="18283-105">如果未播放聲音，就不會發生任何事。</span><span class="sxs-lookup"><span data-stu-id="18283-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18283-106">範例</span><span class="sxs-lookup"><span data-stu-id="18283-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18283-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="18283-107">Compiling the Code</span></span>  
 <span data-ttu-id="18283-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="18283-108">This example requires:</span></span>  
  
- <span data-ttu-id="18283-109">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="18283-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="18283-110">您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="18283-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="18283-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="18283-111">Robust Programming</span></span>  
 <span data-ttu-id="18283-112">檔案作業應含括在適當的例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="18283-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="18283-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="18283-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="18283-114">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="18283-114">The path name is malformed.</span></span> <span data-ttu-id="18283-115">例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="18283-115">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="18283-116">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="18283-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="18283-117">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="18283-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="18283-118">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="18283-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="18283-119">路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="18283-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="18283-120">此路徑只是一個冒號 ":" (<xref:System.NotSupportedException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="18283-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="18283-121">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="18283-121">.NET Framework Security</span></span>  
 <span data-ttu-id="18283-122">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="18283-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="18283-123">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="18283-123">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="18283-124">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="18283-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18283-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18283-125">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="18283-126">如何：從 Windows Form 播放的音效</span><span class="sxs-lookup"><span data-stu-id="18283-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="18283-127">SoundPlayer 類別概觀</span><span class="sxs-lookup"><span data-stu-id="18283-127">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
