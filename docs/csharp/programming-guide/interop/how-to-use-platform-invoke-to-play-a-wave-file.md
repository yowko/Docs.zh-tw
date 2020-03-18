---
title: 如何使用平台叫用來播放 WAV 檔 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 3ea90f0739ad45c31e4f25836c9de8e708dff2cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700818"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>如何使用平台叫用來播放 WAV 檔（C# 程式設計指南）

以下 C# 代碼示例說明了如何使用平台叫用服務在 Windows 作業系統上播放 WAV 音效檔。

## <a name="example"></a>範例

這個範例程式碼會使用 <xref:System.Runtime.InteropServices.DllImportAttribute>，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。 這個範例包含具有按鈕的簡單 Windows Form。 按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。 選擇波形檔時，使用`PlaySound()`*winmm.dll*庫的方法播放它。 如需此方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files) (於波形音訊檔案使用 PlaySound 函式)。 瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]****，以使用平台叫用來播放音訊檔案。 文字方塊會顯示所選取檔案的完整路徑。

透過篩選設定來篩選 [開啟檔案]**** 對話方塊，使其只顯示副檔名為 .wav 的檔案︰

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>編譯程式碼

1. 在視覺化工作室中創建新的 C# Windows 表單應用程式專案，並將其命名為**WinSound**。

2. 複製上面的代碼，並將其粘貼到*Form1.cs*檔的內容上。

3. 複製以下代碼，並將其粘貼到*Form1.Designer.cs*檔中，在方法中`InitializeComponent()`，在任何現有代碼之後。

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. 編譯並執行程式碼。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [互通性概觀](interoperability-overview.md)
- [進一步了解平台叫用](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [使用平台叫用封送處理資料](../../../framework/interop/marshaling-data-with-platform-invoke.md)
