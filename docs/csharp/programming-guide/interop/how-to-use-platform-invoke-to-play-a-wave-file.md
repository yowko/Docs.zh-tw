---
title: "如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2aacad0e8004e60471a59ebef695ddae5f7a2a7d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)
下列 C# 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。  
  
## <a name="example"></a>範例  
 這個範例程式碼會使用 `DllImport`，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。 這個範例包含具有按鈕的簡單 Windows Form。 按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。 選取音訊檔案時，會使用 winmm.DLL 組件方法的 `PlaySound()` 方法進行播放。 如需 winmm.dll 之 `PlaySound` 方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553) (搭配使用 PlaySound 函式與波形音訊檔案)。 瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]，以使用平台叫用來播放音訊檔案。 文字方塊會顯示所選取檔案的完整路徑。  
  
 透過篩選設定來篩選 [開啟檔案] 對話方塊，使其只顯示副檔名為 .wav 的檔案︰  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
### <a name="to-compile-the-code"></a>編譯程式碼  
  
1.  在 Visual Studio 中建立新的 C# Windows 應用程式專案，並將它命名為 **WinSound**。  
  
2.  複製上述程式碼，並將它貼至 `Form1.cs` 檔案的內容上。  
  
3.  複製下列程式碼，並將它貼入 `Form1.Designer.cs` 檔案之 `InitializeComponent()` 方法中的任何現有程式碼後面。  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  編譯並執行程式碼。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如需詳細資訊，請參閱 [.NET Framework 安全性](http://go.microsoft.com/fwlink/?LinkId=37122)。  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 [詳述平台叫用](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [使用平台叫用封送處理資料](../../../framework/interop/marshaling-data-with-platform-invoke.md)
