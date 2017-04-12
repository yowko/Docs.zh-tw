---
title: "播放音效 (Visual Basic) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ed4ee0a09067900a6bead04abec02f141936ba42
ms.lasthandoff: 03/13/2017

---
# <a name="playing-sounds-visual-basic"></a>播放音效 (Visual Basic)
`My.Computer.Audio` 物件提供播放音效的方法。  
  
## <a name="playing-sounds"></a>播放音效  
 背景播放可讓應用程式在播放音效時執行其他程式碼。 `My.Computer.Audio.Play` 方法可讓應用程式一次只播放一種背景音效，當應用程式播放新的背景音效時，就會停止播放先前的背景音效。 您也可以播放音效，並等候它播放完畢。  
  
 在下例中，`My.Computer.Audio.Play` 方法會播放音效。 當指定 `AudioPlayMode.WaitToComplete` 時，`My.Computer.Audio.Play` 會等待音效播放完畢再呼叫程式碼繼續執行。 使用此例時，您應該確保檔案名稱指向您電腦上的 .wav 音效檔。  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 在下例中，`My.Computer.Audio.Play` 方法會播放音效。 使用此例時，您應該確保應用程式資源包含名為瀑布的 .wav 音效檔。  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>循環播放音效  
 在下例中，`My.Computer.Audio.Play` 方法會在指定 `PlayMode.BackgroundLoop` 時於背景播放指定的音效。 使用此例時，您應該確保檔案名稱指向您電腦上的 .wav 音效檔。  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 在下例中，`My.Computer.Audio.Play` 方法會在指定 `PlayMode.BackgroundLoop` 時於背景播放指定的音效。 使用此例時，您應該確保應用程式資源包含名為瀑布的 .wav 音效檔。  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 上述程式碼範例也提供為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [音效]**** 中。 如需詳細資訊，請參閱[程式碼片段](https://docs.microsoft.com/visualstudio/ide/code-snippets)。  
  
 一般而言，當應用程式循環播放音效時，最後應該會停止音效。  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>在背景停止播放音效  
 使用 `My.Computer.Audio.Stop` 方法來停止應用程式目前在背景播放或循環播放的音效。  
  
 一般而言，當應用程式循環播放音效時，應該會在某個時間點停止音效。  
  
 下例會停止在背景中播放的音效。  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 上述程式碼範例也提供為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows Forms 應用程式] > [音效]**** 中。 如需詳細資訊，請參閱[程式碼片段](https://docs.microsoft.com/visualstudio/ide/code-snippets)。  
  
## <a name="playing-system-sounds"></a>播放系統音效  
 使用 `My.Computer.Audio.PlaySystemSound` 方法播放指定的系統音效。  
  
 `My.Computer.Audio.PlaySystemSound` 方法接受 <xref:System.Media.SystemSound> 類別其中一個共用成員作為參數。 系統音效 <xref:System.Media.SystemSounds.Asterisk%2A> 通常表示錯誤。  
  
 下例會使用 `My.Computer.Audio.PlaySystemSound` 方法播放系統音效。  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>
