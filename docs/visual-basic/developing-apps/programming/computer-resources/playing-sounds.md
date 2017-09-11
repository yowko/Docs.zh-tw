---
title: "播放音效 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: a15efff54bd54fdaced6c741cd6acf5c8b544cdd
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="d8fd6-102">播放音效 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8fd6-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="d8fd6-103">`My.Computer.Audio` 物件提供播放音效的方法。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="d8fd6-104">播放音效</span><span class="sxs-lookup"><span data-stu-id="d8fd6-104">Playing Sounds</span></span>  
 <span data-ttu-id="d8fd6-105">背景播放可讓應用程式在播放音效時執行其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="d8fd6-106">`My.Computer.Audio.Play` 方法可讓應用程式一次只播放一種背景音效，當應用程式播放新的背景音效時，就會停止播放先前的背景音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="d8fd6-107">您也可以播放音效，並等候它播放完畢。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="d8fd6-108">在下例中，`My.Computer.Audio.Play` 方法會播放音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="d8fd6-109">當指定 `AudioPlayMode.WaitToComplete` 時，`My.Computer.Audio.Play` 會等待音效播放完畢再呼叫程式碼繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="d8fd6-110">使用此例時，您應該確保檔案名稱指向您電腦上的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 <span data-ttu-id="d8fd6-111">[!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8fd6-111">[!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]</span></span>  
  
 <span data-ttu-id="d8fd6-112">在下例中，`My.Computer.Audio.Play` 方法會播放音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-112">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="d8fd6-113">使用此例時，您應該確保應用程式資源包含名為瀑布的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-113">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 <span data-ttu-id="d8fd6-114">[!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8fd6-114">[!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]</span></span>  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="d8fd6-115">循環播放音效</span><span class="sxs-lookup"><span data-stu-id="d8fd6-115">Playing Looping Sounds</span></span>  
 <span data-ttu-id="d8fd6-116">在下例中，`My.Computer.Audio.Play` 方法會在指定 `PlayMode.BackgroundLoop` 時於背景播放指定的音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="d8fd6-117">使用此例時，您應該確保檔案名稱指向您電腦上的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-117">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 <span data-ttu-id="d8fd6-118">[!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8fd6-118">[!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]</span></span>  
  
 <span data-ttu-id="d8fd6-119">在下例中，`My.Computer.Audio.Play` 方法會在指定 `PlayMode.BackgroundLoop` 時於背景播放指定的音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-119">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="d8fd6-120">使用此例時，您應該確保應用程式資源包含名為瀑布的 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-120">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 <span data-ttu-id="d8fd6-121">[!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8fd6-121">[!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]</span></span>  
  
 <span data-ttu-id="d8fd6-122">上述程式碼範例也提供為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-122">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="d8fd6-123">在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [音效] 中。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-123">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="d8fd6-124">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-124">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="d8fd6-125">一般而言，當應用程式循環播放音效時，最後應該會停止音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-125">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="d8fd6-126">在背景停止播放音效</span><span class="sxs-lookup"><span data-stu-id="d8fd6-126">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="d8fd6-127">使用 `My.Computer.Audio.Stop` 方法來停止應用程式目前在背景播放或循環播放的音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-127">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="d8fd6-128">一般而言，當應用程式循環播放音效時，應該會在某個時間點停止音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-128">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="d8fd6-129">下例會停止在背景中播放的音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-129">The following example stops a sound that is playing in the background.</span></span>  
  
 <span data-ttu-id="d8fd6-130">[!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8fd6-130">[!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]</span></span>  
  
 <span data-ttu-id="d8fd6-131">上述程式碼範例也提供為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-131">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="d8fd6-132">在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [音效] 中。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-132">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="d8fd6-133">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-133">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="d8fd6-134">播放系統音效</span><span class="sxs-lookup"><span data-stu-id="d8fd6-134">Playing System Sounds</span></span>  
 <span data-ttu-id="d8fd6-135">使用 `My.Computer.Audio.PlaySystemSound` 方法播放指定的系統音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-135">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="d8fd6-136">`My.Computer.Audio.PlaySystemSound` 方法接受 <xref:System.Media.SystemSound> 類別其中一個共用成員作為參數。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-136">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="d8fd6-137">系統音效 <xref:System.Media.SystemSounds.Asterisk%2A> 通常表示錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-137">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="d8fd6-138">下例會使用 `My.Computer.Audio.PlaySystemSound` 方法播放系統音效。</span><span class="sxs-lookup"><span data-stu-id="d8fd6-138">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 <span data-ttu-id="d8fd6-139">[!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8fd6-139">[!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fd6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8fd6-140">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>

