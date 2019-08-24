---
title: HOW TO：播放 Windows Forms 的音效
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
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015805"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="0bac9-102">作法：播放 Windows Forms 的音效</span><span class="sxs-lookup"><span data-stu-id="0bac9-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="0bac9-103">這個範例會在執行階段播放所指定路徑的音效。</span><span class="sxs-lookup"><span data-stu-id="0bac9-103">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="0bac9-104">範例</span><span class="sxs-lookup"><span data-stu-id="0bac9-104">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="0bac9-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0bac9-105">Compiling the Code</span></span>
 <span data-ttu-id="0bac9-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0bac9-106">This example requires:</span></span>

- <span data-ttu-id="0bac9-107">您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0bac9-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="0bac9-108">(C#) <xref:System.Media?displayProperty=nameWithType>命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="0bac9-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="0bac9-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0bac9-109">Robust Programming</span></span>
 <span data-ttu-id="0bac9-110">檔案作業應該含括在適當的結構化例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="0bac9-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="0bac9-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="0bac9-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="0bac9-112">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="0bac9-112">The path name is malformed.</span></span> <span data-ttu-id="0bac9-113">舉例來說，其可能包含非法的字元，或是只有空白字元 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="0bac9-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="0bac9-114">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="0bac9-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="0bac9-115">路徑名稱是 `null` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="0bac9-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="0bac9-116">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="0bac9-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="0bac9-117">路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="0bac9-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="0bac9-118">路徑只是一個冒號 ":" (<xref:System.NotSupportedException>類別)。</span><span class="sxs-lookup"><span data-stu-id="0bac9-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="0bac9-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="0bac9-119">.NET Framework Security</span></span>
 <span data-ttu-id="0bac9-120">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="0bac9-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="0bac9-121">例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="0bac9-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="0bac9-122">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="0bac9-122">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bac9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bac9-123">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="0bac9-124">如何：在 Windows Form 中以非同步方式載入音效</span><span class="sxs-lookup"><span data-stu-id="0bac9-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
