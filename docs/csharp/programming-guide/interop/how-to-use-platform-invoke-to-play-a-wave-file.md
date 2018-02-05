---
title: "如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 10c2490255565de872396a0155bb588f9d696b24
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="fa0b9-102">如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="fa0b9-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="fa0b9-103">下列 C# 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa0b9-104">範例</span><span class="sxs-lookup"><span data-stu-id="fa0b9-104">Example</span></span>  
 <span data-ttu-id="fa0b9-105">這個範例程式碼會使用 `DllImport`，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="fa0b9-106">這個範例包含具有按鈕的簡單 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="fa0b9-107">按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="fa0b9-108">選取音訊檔案時，會使用 winmm.DLL 組件方法的 `PlaySound()` 方法進行播放。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="fa0b9-109">如需 winmm.dll 之 `PlaySound` 方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx) (搭配使用 PlaySound 函式與波形音訊檔案)。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](https://msdn.microsoft.com/library/aa910379.aspx).</span></span> <span data-ttu-id="fa0b9-110">瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]，以使用平台叫用來播放音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="fa0b9-111">文字方塊會顯示所選取檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="fa0b9-112">透過篩選設定來篩選 [開啟檔案] 對話方塊，使其只顯示副檔名為 .wav 的檔案︰</span><span class="sxs-lookup"><span data-stu-id="fa0b9-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa0b9-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fa0b9-113">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="fa0b9-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fa0b9-114">To compile the code</span></span>  
  
1.  <span data-ttu-id="fa0b9-115">在 Visual Studio 中建立新的 C# Windows 應用程式專案，並將它命名為 **WinSound**。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-115">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="fa0b9-116">複製上述程式碼，並將它貼至 `Form1.cs` 檔案的內容上。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-116">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="fa0b9-117">複製下列程式碼，並將它貼入 `Form1.Designer.cs` 檔案之 `InitializeComponent()` 方法中的任何現有程式碼後面。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-117">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  <span data-ttu-id="fa0b9-118">編譯並執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-118">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fa0b9-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="fa0b9-119">.NET Framework Security</span></span>  
 <span data-ttu-id="fa0b9-120">如需詳細資訊，請參閱 [.NET Framework 安全性](https://technet.microsoft.com/en-us/security/)。</span><span class="sxs-lookup"><span data-stu-id="fa0b9-120">For more information, see [.NET Framework Security](https://technet.microsoft.com/en-us/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa0b9-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa0b9-121">See Also</span></span>  
 [<span data-ttu-id="fa0b9-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fa0b9-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa0b9-123">互通性概觀</span><span class="sxs-lookup"><span data-stu-id="fa0b9-123">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [<span data-ttu-id="fa0b9-124">詳述平台叫用</span><span class="sxs-lookup"><span data-stu-id="fa0b9-124">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
 [<span data-ttu-id="fa0b9-125">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="fa0b9-125">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
