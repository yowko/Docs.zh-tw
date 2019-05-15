---
title: 作法：在 Windows Forms 中以非同步方式載入音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 5f533d82fcca07a2b64bdbbfb160a7b2a23ce540
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592368"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="27639-102">作法：在 Windows Forms 中以非同步方式載入音效</span><span class="sxs-lookup"><span data-stu-id="27639-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="27639-103">下列程式碼範例會以非同步方式從 URL 載入音效，然後在新的執行緒上播放。</span><span class="sxs-lookup"><span data-stu-id="27639-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27639-104">範例</span><span class="sxs-lookup"><span data-stu-id="27639-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27639-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="27639-105">Compiling the Code</span></span>  
 <span data-ttu-id="27639-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="27639-106">This example requires:</span></span>  
  
- <span data-ttu-id="27639-107">本系統和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="27639-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="27639-108">您將檔案名稱 `"http://www.tailspintoys.com/sounds/stop.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="27639-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="27639-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="27639-109">Robust Programming</span></span>  
 <span data-ttu-id="27639-110">檔案作業應含括在適當的例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="27639-110">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="27639-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="27639-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="27639-112">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="27639-112">The path name is malformed.</span></span> <span data-ttu-id="27639-113">例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="27639-113">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="27639-114">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="27639-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="27639-115">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="27639-115">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="27639-116">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="27639-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="27639-117">此路徑無效 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="27639-117">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="27639-118">此路徑只是一個冒號 ":" (<xref:System.NotSupportedException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="27639-118">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="27639-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="27639-119">.NET Framework Security</span></span>  
 <span data-ttu-id="27639-120">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="27639-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="27639-121">例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="27639-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="27639-122">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="27639-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27639-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27639-123">See also</span></span>

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="27639-124">如何：從 Windows Form 播放的音效</span><span class="sxs-lookup"><span data-stu-id="27639-124">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
