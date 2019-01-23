---
title: HOW TO：從 Windows Form 播放的音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 02b0cb2952e11946f994819bb09a55167781137c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607247"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="1a3c8-102">HOW TO：從 Windows Form 播放的音效</span><span class="sxs-lookup"><span data-stu-id="1a3c8-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="1a3c8-103">這個範例會在執行階段播放所指定路徑的音效。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a3c8-104">範例</span><span class="sxs-lookup"><span data-stu-id="1a3c8-104">Example</span></span>  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a3c8-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1a3c8-105">Compiling the Code</span></span>  
 <span data-ttu-id="1a3c8-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1a3c8-106">This example requires:</span></span>  
  
-   <span data-ttu-id="1a3c8-107">您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="1a3c8-108">(C#) 的參考<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1a3c8-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1a3c8-109">Robust Programming</span></span>  
 <span data-ttu-id="1a3c8-110">檔案作業應該含括在適當的結構化例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="1a3c8-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="1a3c8-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1a3c8-112">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-112">The path name is malformed.</span></span> <span data-ttu-id="1a3c8-113">舉例來說，其可能包含非法的字元，或是只有空白字元 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="1a3c8-114">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="1a3c8-115">路徑名稱是 `null` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="1a3c8-116">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="1a3c8-117">路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="1a3c8-118">路徑是只有冒號":"(<xref:System.NotSupportedException>類別)。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1a3c8-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1a3c8-119">.NET Framework Security</span></span>  
 <span data-ttu-id="1a3c8-120">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="1a3c8-121">例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="1a3c8-122">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="1a3c8-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3c8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a3c8-123">See also</span></span>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="1a3c8-124">如何：在 Windows Form 中的非同步載入音效</span><span class="sxs-lookup"><span data-stu-id="1a3c8-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)

