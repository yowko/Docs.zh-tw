---
title: 作法：循環播放 Windows Forms 的音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592354"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>作法：循環播放 Windows Forms 的音效
下列程式碼範例會重複播放音效。 當 `stopPlayingButton_Click` 事件處理常式中的程式碼執行時，會停止目前正在播放任何聲音。 如果未播放聲音，就不會發生任何事。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 本系統和 System.Windows.Forms 組件的參考。  
  
- 您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。  
  
## <a name="robust-programming"></a>穩固程式設計  
 檔案作業應含括在適當的例外狀況處理區塊內。  
  
 以下條件可能會造成例外狀況：  
  
- 路徑名稱的格式不正確。 例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。  
  
- 路徑是唯讀的 (<xref:System.IO.IOException> 類別)。  
  
- 路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。  
  
- 路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。  
  
- 路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。  
  
- 此路徑只是一個冒號 ":" (<xref:System.NotSupportedException> 類別)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請勿根據檔案名稱來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [如何：從 Windows Form 播放的音效](how-to-play-a-sound-from-a-windows-form.md)
- [SoundPlayer 類別概觀](soundplayer-class-overview.md)
