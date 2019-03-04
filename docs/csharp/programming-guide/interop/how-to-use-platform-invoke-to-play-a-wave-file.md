---
title: 作法：使用平台叫用播放 WAV 檔 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 209a0f03197e0f77e23be0dc1170789688f3e09a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967213"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>作法：使用平台叫用播放 WAV 檔 (C# 程式設計指南)
下列 C# 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。  
  
## <a name="example"></a>範例  
 這個範例程式碼會使用 `DllImport`，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。 這個範例包含具有按鈕的簡單 Windows Form。 按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。 選取 WAV 檔時，會使用 `winmm.dll` 程式庫的 `PlaySound()` 方法播放。 如需此方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files) (於波形音訊檔案使用 PlaySound 函式)。 瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]，以使用平台叫用來播放音訊檔案。 文字方塊會顯示所選取檔案的完整路徑。  
  
 透過篩選設定來篩選 [開啟檔案] 對話方塊，使其只顯示副檔名為 .wav 的檔案︰  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
### <a name="to-compile-the-code"></a>編譯程式碼  
  
1.  在 Visual Studio 中建立新的 C# Windows 應用程式專案，並將它命名為 **WinSound**。  
  
2.  複製上述程式碼，並將它貼至 `Form1.cs` 檔案的內容上。  
  
3.  複製下列程式碼，並將它貼入 `Form1.Designer.cs` 檔案之 `InitializeComponent()` 方法中的任何現有程式碼後面。  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4.  編譯並執行程式碼。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如需詳細資訊，請參閱 [.NET 的安全性](../../../standard/security/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)
- [詳述平台叫用](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [使用平台叫用封送處理資料](../../../framework/interop/marshaling-data-with-platform-invoke.md)
