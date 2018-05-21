---
title: 播放音效 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: decd845fde5bd4fad702cfe05fd63fcc180b63a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="3c89a-102">播放音效 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c89a-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="3c89a-103">`My.Computer.Audio` 物件提供播放音效的方法。</span><span class="sxs-lookup"><span data-stu-id="3c89a-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="3c89a-104">播放音效</span><span class="sxs-lookup"><span data-stu-id="3c89a-104">Playing Sounds</span></span>  
 <span data-ttu-id="3c89a-105">背景播放可讓應用程式在播放音效時執行其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="3c89a-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="3c89a-106">`My.Computer.Audio.Play` 方法可讓應用程式一次只播放一種背景音效，當應用程式播放新的背景音效時，就會停止播放先前的背景音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="3c89a-107">您也可以播放音效，並等候它播放完畢。</span><span class="sxs-lookup"><span data-stu-id="3c89a-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="3c89a-108">在下例中，`My.Computer.Audio.Play` 方法會播放音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="3c89a-109">當指定 `AudioPlayMode.WaitToComplete` 時，`My.Computer.Audio.Play` 會等待音效播放完畢再呼叫程式碼繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3c89a-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="3c89a-110">使用此例時，您應該確保檔案名稱指向您電腦上的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="3c89a-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 <span data-ttu-id="3c89a-111">在下例中，`My.Computer.Audio.Play` 方法會播放音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="3c89a-112">使用此例時，您應該確保應用程式資源包含名為瀑布的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="3c89a-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="3c89a-113">循環播放音效</span><span class="sxs-lookup"><span data-stu-id="3c89a-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="3c89a-114">在下例中，`My.Computer.Audio.Play` 方法會在指定 `PlayMode.BackgroundLoop` 時於背景播放指定的音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="3c89a-115">使用此例時，您應該確保檔案名稱指向您電腦上的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="3c89a-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 <span data-ttu-id="3c89a-116">在下例中，`My.Computer.Audio.Play` 方法會在指定 `PlayMode.BackgroundLoop` 時於背景播放指定的音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="3c89a-117">使用此例時，您應該確保應用程式資源包含名為瀑布的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="3c89a-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 <span data-ttu-id="3c89a-118">上述程式碼範例也提供為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="3c89a-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3c89a-119">在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [音效] 中。</span><span class="sxs-lookup"><span data-stu-id="3c89a-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="3c89a-120">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="3c89a-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="3c89a-121">一般而言，當應用程式循環播放音效時，最後應該會停止音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="3c89a-122">在背景停止播放音效</span><span class="sxs-lookup"><span data-stu-id="3c89a-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="3c89a-123">使用 `My.Computer.Audio.Stop` 方法來停止應用程式目前在背景播放或循環播放的音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="3c89a-124">一般而言，當應用程式循環播放音效時，應該會在某個時間點停止音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="3c89a-125">下例會停止在背景中播放的音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 <span data-ttu-id="3c89a-126">上述程式碼範例也提供為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="3c89a-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3c89a-127">在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [音效] 中。</span><span class="sxs-lookup"><span data-stu-id="3c89a-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="3c89a-128">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="3c89a-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="3c89a-129">播放系統音效</span><span class="sxs-lookup"><span data-stu-id="3c89a-129">Playing System Sounds</span></span>  
 <span data-ttu-id="3c89a-130">使用 `My.Computer.Audio.PlaySystemSound` 方法播放指定的系統音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="3c89a-131">`My.Computer.Audio.PlaySystemSound` 方法接受 <xref:System.Media.SystemSound> 類別其中一個共用成員作為參數。</span><span class="sxs-lookup"><span data-stu-id="3c89a-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="3c89a-132">系統音效 <xref:System.Media.SystemSounds.Asterisk%2A> 通常表示錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c89a-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="3c89a-133">下例會使用 `My.Computer.Audio.PlaySystemSound` 方法播放系統音效。</span><span class="sxs-lookup"><span data-stu-id="3c89a-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3c89a-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c89a-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
