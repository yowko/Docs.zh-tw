---
title: 如何：播放 Windows Form 中的音效
description: 瞭解如何在執行時間于指定的路徑播放 Windows Form 中的音效。 此外，您也可以瞭解如何編譯器代碼和 .NET 安全性架構。
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
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613744"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="2ab9d-104">如何：播放 Windows Form 中的音效</span><span class="sxs-lookup"><span data-stu-id="2ab9d-104">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="2ab9d-105">這個範例會在執行階段播放所指定路徑的音效。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-105">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="2ab9d-106">範例</span><span class="sxs-lookup"><span data-stu-id="2ab9d-106">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="2ab9d-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2ab9d-107">Compiling the Code</span></span>
 <span data-ttu-id="2ab9d-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2ab9d-108">This example requires:</span></span>

- <span data-ttu-id="2ab9d-109">您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-109">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="2ab9d-110">編寫命名空間的參考 <xref:System.Media?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-110">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="2ab9d-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2ab9d-111">Robust Programming</span></span>
 <span data-ttu-id="2ab9d-112">檔案作業應該含括在適當的結構化例外狀況處理區塊內。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-112">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="2ab9d-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2ab9d-113">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="2ab9d-114">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-114">The path name is malformed.</span></span> <span data-ttu-id="2ab9d-115">舉例來說，其可能包含非法的字元，或是只有空白字元 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-115">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="2ab9d-116">路徑是唯讀的 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="2ab9d-117">路徑名稱是 `null` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-117">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="2ab9d-118">路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="2ab9d-119">路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="2ab9d-120">路徑只是一個冒號 "：" （ <xref:System.NotSupportedException> 類別）。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-120">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="2ab9d-121">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="2ab9d-121">.NET Framework Security</span></span>
 <span data-ttu-id="2ab9d-122">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="2ab9d-123">例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="2ab9d-124">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="2ab9d-124">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ab9d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ab9d-125">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="2ab9d-126">如何：在 Windows Forms 中以非同步方式載入音效</span><span class="sxs-lookup"><span data-stu-id="2ab9d-126">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
