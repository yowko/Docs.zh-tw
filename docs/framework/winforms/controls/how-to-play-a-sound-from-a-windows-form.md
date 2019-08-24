---
title: HOW TO：播放 Windows Forms 的音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015805"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>作法：播放 Windows Forms 的音效
這個範例會在執行階段播放所指定路徑的音效。

## <a name="example"></a>範例

```vb
Sub PlaySimpleSound()
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")
End Sub
```

```csharp
private void playSimpleSound()
{
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");
    simpleSound.Play();
}
```

## <a name="compiling-the-code"></a>編譯程式碼
 這個範例需要：

- 您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。

- (C#) <xref:System.Media?displayProperty=nameWithType>命名空間的參考。

## <a name="robust-programming"></a>穩固程式設計
 檔案作業應該含括在適當的結構化例外狀況處理區塊內。

 以下條件可能會造成例外狀況：

- 路徑名稱的格式不正確。 舉例來說，其可能包含非法的字元，或是只有空白字元 (<xref:System.ArgumentException> 類別)。

- 路徑是唯讀的 (<xref:System.IO.IOException> 類別)。

- 路徑名稱是 `null` (<xref:System.ArgumentNullException> 類別)。

- 路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。

- 路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。

- 路徑只是一個冒號 ":" (<xref:System.NotSupportedException>類別)。

## <a name="net-framework-security"></a>.NET Framework 安全性
 請勿根據檔案名稱來判斷檔案內容。 例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。

## <a name="see-also"></a>另請參閱

- <xref:System.Media.SoundPlayer>
- [如何：在 Windows Form 中以非同步方式載入音效](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
