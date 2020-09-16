---
title: '如何使用平台叫用播放 WAV 檔-c # 程式設計指南'
description: '這個 c # 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 WAV 音效檔。'
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6f507fa348bf1ea1b3fc5c3a868a6fbab7f8ec56
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558351"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="c5282-103">如何使用平台叫用播放 WAV 檔 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="c5282-103">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="c5282-104">下列 c # 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 WAV 音效檔。</span><span class="sxs-lookup"><span data-stu-id="c5282-104">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="c5282-105">範例</span><span class="sxs-lookup"><span data-stu-id="c5282-105">Example</span></span>

<span data-ttu-id="c5282-106">這個範例程式碼會使用 <xref:System.Runtime.InteropServices.DllImportAttribute>，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。</span><span class="sxs-lookup"><span data-stu-id="c5282-106">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="c5282-107">這個範例包含具有按鈕的簡單 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="c5282-107">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="c5282-108">按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。</span><span class="sxs-lookup"><span data-stu-id="c5282-108">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="c5282-109">選取 wave 檔案時，會使用winmm.dll程式庫的方法來播放該檔案 `PlaySound()` 。 *winmm.dll*</span><span class="sxs-lookup"><span data-stu-id="c5282-109">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="c5282-110">如需此方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files) (於波形音訊檔案使用 PlaySound 函式)。</span><span class="sxs-lookup"><span data-stu-id="c5282-110">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="c5282-111">瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]\*\*\*\*，以使用平台叫用來播放音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="c5282-111">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="c5282-112">文字方塊會顯示所選取檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c5282-112">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="c5282-113">透過篩選設定來篩選 [開啟檔案]\*\*\*\* 對話方塊，使其只顯示副檔名為 .wav 的檔案︰</span><span class="sxs-lookup"><span data-stu-id="c5282-113">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="c5282-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c5282-114">Compiling the code</span></span>

1. <span data-ttu-id="c5282-115">在 Visual Studio 中建立新的 c # Windows Forms 應用程式專案，並將它命名為 **WinSound**。</span><span class="sxs-lookup"><span data-stu-id="c5282-115">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="c5282-116">複製上述程式碼，並將它貼到 *Form1.cs* 檔案的內容上。</span><span class="sxs-lookup"><span data-stu-id="c5282-116">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="c5282-117">複製下列程式碼，並將它貼入 *Form1.Designer.cs* 檔案的方法中，在 `InitializeComponent()` 任何現有的程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="c5282-117">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="c5282-118">編譯並執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5282-118">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5282-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5282-119">See also</span></span>

- [<span data-ttu-id="c5282-120">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c5282-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c5282-121">互通性概觀</span><span class="sxs-lookup"><span data-stu-id="c5282-121">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="c5282-122">進一步了解平台叫用</span><span class="sxs-lookup"><span data-stu-id="c5282-122">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="c5282-123">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="c5282-123">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
