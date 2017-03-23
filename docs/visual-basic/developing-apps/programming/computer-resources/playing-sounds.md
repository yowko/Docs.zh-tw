---
title: "Playing Sounds (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "system sounds, playing"
  - "system sounds"
  - "playing sounds, Visual Basic"
  - "sound loops"
  - "My.Computer.Audio object, tasks"
  - "sounds, playing"
  - "sounds, background"
  - "playing sounds"
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Playing Sounds (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`My.Computer.Audio` 物件會提供用於播放音效的方法。  
  
## 播放音效  
 背景播放方式可讓應用程式於播放音效時執行其他程式碼。  `My.Computer.Audio.Play` 方法可以讓應用程式一次只播放一種背景音效，當應用程式播放新的背景音效時，即會停止播放前一個背景音效。  您也可以播放音效並等待它完成。  
  
 在下列範例中， `My.Computer.Audio.Play`方法會播放聲音。  指定 `AudioPlayMode.WaitToComplete` 時，`My.Computer.Audio.Play` 會等候音效播放完成，再呼叫程式碼繼續執行。  當使用這個範例中，您應該確定檔案名稱是指在您的電腦上的.wav 音效檔  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 在下列範例中， `My.Computer.Audio.Play`方法會播放聲音。  當使用這個範例中，您應該確定包含名為瀑布的.wav 音效檔的應用程式資源。  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## 播放循環音效  
 在下列範例中， `My.Computer.Audio.Play`方法會在背景播放指定的音效時`PlayMode.BackgroundLoop`所指定。  當使用這個範例中，您應該確定檔案名稱是指在您的電腦上的.wav 音效檔。  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 在下列範例中， `My.Computer.Audio.Play`方法會在背景播放指定的音效時`PlayMode.BackgroundLoop`所指定。  當使用這個範例中，您應該確定包含名為瀑布的.wav 音效檔的應用程式資源。  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 先前的程式碼範例也是 IntelliSense 的程式碼的程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**Windows Form 應用程式 \> 聲音**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
 一般而言，當應用程式播放重複循環音效時，它最後應該停止該音效。  
  
## 停止在背景音效的播放  
 使用 `My.Computer.Audio.Stop` 方法，停止應用程式目前正在播放的背景或重複循環音效。  
  
 一般而言，當應用程式播放重複循環音效時，應該會在某一點停止音效。  
  
 下列範例會停止在背景播放音效。  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 先前的程式碼範例也是 IntelliSense 的程式碼的程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**Windows Form 應用程式 \> 聲音**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
## 播放系統音效  
 使用 `My.Computer.Audio.PlaySystemSound` 方法以播放指定的系統音效。  
  
 `My.Computer.Audio.PlaySystemSound` 方法會採用 <xref:System.Media.SystemSound> 類別的其中一個共用成員做為參數。  系統音效 <xref:System.Media.SystemSounds.Asterisk%2A> 通常會代表錯誤。  
  
 下列範例會使用`My.Computer.Audio.PlaySystemSound`方法，以播放系統音效。  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>