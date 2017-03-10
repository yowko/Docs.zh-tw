---
title: "如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ".wav 檔案"
  - "互通性 [C#], 使用 Pinvoke 播放 WAV 檔案"
  - "平台叫用, 音效檔"
  - "wav 檔案"
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)
下列 C\# 程式碼範例會示範如何在 Windows 作業系統上，使用平台叫用服務播放 WAV 音效檔。  
  
## 範例  
 在下面的程式碼中，會使用 `DllImport` 將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。  這是以簡單的 Windows Form 再加上一個按鈕為例。  按一下按鈕，隨即開啟標準的 Windows <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您開啟想要播放的檔案。  選取了 WAV 檔之後，便會使用 winmm.DLL 組件方法的 `PlaySound()` 方法播放。  如需 winmm.dll 之 `PlaySound` 方法的詳細資訊，請參閱[搭配波形音效檔使用 PlaySound 函式](http://go.microsoft.com/fwlink/?LinkId=148553) \(英文\)。  瀏覽並選取副檔名為 .wav 的檔案，然後按一下 \[**開啟**\] 以平台叫用播放 WAV 檔。  文字方塊會顯示所選取檔案的完整路徑。  
  
 \[**開啟檔案**\] 對話方塊會透過篩選設定，只顯示副檔名為 .wav 的檔案：  
  
 [!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/csharp/how-to-use-platform-invo_1.cs)]  
  
 [!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/csharp/how-to-use-platform-invo_2.cs)]  
  
## 編譯程式碼  
  
### 若要編譯程式碼  
  
1.  在 Visual Studio 中建立新的 C\# Windows 應用程式專案，並命名為 WinSound。  
  
2.  複製上面的程式碼，將其貼於 `Form1.cs` 檔的內容中。  
  
3.  複製下列程式碼，然後將其貼在 `Form1.Designer.cs` 檔的 `InitializeComponent()` 方法中 \(在現有的任何程式碼後\)。  
  
     [!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/csharp/how-to-use-platform-invo_3.cs)]  
  
4.  編譯並執行程式碼。  
  
## .NET Framework 安全性  
 如需詳細資訊，請參閱 [.NET Framework 安全性](http://msdn2.microsoft.com/zh-tw/security/aa570406.aspx) \(英文\)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/zh-tw/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [使用平台叫用封送處理資料](../Topic/Marshaling%20Data%20with%20Platform%20Invoke.md)