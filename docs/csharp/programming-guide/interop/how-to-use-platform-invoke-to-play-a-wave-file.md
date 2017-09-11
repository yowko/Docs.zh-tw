---
title: "如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 001236392d2b3d3c70dbd0faf2a899929dfe8625
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="8eb28-102">如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8eb28-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="8eb28-103">下列 C# 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="8eb28-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eb28-104">範例</span><span class="sxs-lookup"><span data-stu-id="8eb28-104">Example</span></span>  
 <span data-ttu-id="8eb28-105">這個範例程式碼會使用 `DllImport`，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。</span><span class="sxs-lookup"><span data-stu-id="8eb28-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="8eb28-106">這個範例包含具有按鈕的簡單 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="8eb28-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="8eb28-107">按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。</span><span class="sxs-lookup"><span data-stu-id="8eb28-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="8eb28-108">選取音訊檔案時，會使用 winmm.DLL 組件方法的 `PlaySound()` 方法進行播放。</span><span class="sxs-lookup"><span data-stu-id="8eb28-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="8eb28-109">如需 winmm.dll 之 `PlaySound` 方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553) (搭配使用 PlaySound 函式與波形音訊檔案)。</span><span class="sxs-lookup"><span data-stu-id="8eb28-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553).</span></span> <span data-ttu-id="8eb28-110">瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]，以使用平台叫用來播放音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="8eb28-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="8eb28-111">文字方塊會顯示所選取檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8eb28-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="8eb28-112">透過篩選設定來篩選 [開啟檔案] 對話方塊，使其只顯示副檔名為 .wav 的檔案︰</span><span class="sxs-lookup"><span data-stu-id="8eb28-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 <span data-ttu-id="8eb28-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8eb28-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span></span>  
  
 <span data-ttu-id="8eb28-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8eb28-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8eb28-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8eb28-115">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="8eb28-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8eb28-116">To compile the code</span></span>  
  
1.  <span data-ttu-id="8eb28-117">在 Visual Studio 中建立新的 C# Windows 應用程式專案，並將它命名為 **WinSound**。</span><span class="sxs-lookup"><span data-stu-id="8eb28-117">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="8eb28-118">複製上述程式碼，並將它貼至 `Form1.cs` 檔案的內容上。</span><span class="sxs-lookup"><span data-stu-id="8eb28-118">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="8eb28-119">複製下列程式碼，並將它貼入 `Form1.Designer.cs` 檔案之 `InitializeComponent()` 方法中的任何現有程式碼後面。</span><span class="sxs-lookup"><span data-stu-id="8eb28-119">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     <span data-ttu-id="8eb28-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8eb28-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span></span>  
  
4.  <span data-ttu-id="8eb28-121">編譯並執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="8eb28-121">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8eb28-122">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8eb28-122">.NET Framework Security</span></span>  
 <span data-ttu-id="8eb28-123">如需詳細資訊，請參閱 [.NET Framework 安全性](http://go.microsoft.com/fwlink/?LinkId=37122)。</span><span class="sxs-lookup"><span data-stu-id="8eb28-123">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb28-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eb28-124">See Also</span></span>  
 <span data-ttu-id="8eb28-125">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8eb28-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8eb28-126">[互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="8eb28-126">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="8eb28-127">[互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="8eb28-127">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="8eb28-128">[詳述平台叫用](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span><span class="sxs-lookup"><span data-stu-id="8eb28-128">[A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span></span>  
 [<span data-ttu-id="8eb28-129">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="8eb28-129">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)

