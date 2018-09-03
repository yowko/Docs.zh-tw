---
title: 如何：在 Windows Form 上循環播放音效
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
ms.openlocfilehash: e6b227915a98bb757b559d229ebc1ee757ffb25c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480113"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>如何：在 Windows Form 上循環播放音效
下列程式碼範例會重複播放音效。 當 `stopPlayingButton_Click` 事件處理常式中的程式碼執行時，會停止目前正在播放任何聲音。 如果未播放聲音，就不會發生任何事。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   本系統和 System.Windows.Forms 組件的參考。  
  
-   您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。  
  
 建置此範例從命令列 visual Basic 或 Visual C# 的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="robust-programming"></a>穩固程式設計  
 檔案作業應含括在適當的例外狀況處理區塊內。  
  
 以下條件可能會造成例外狀況：  
  
-   路徑名稱的格式不正確。 例如，其包含的字元無效，或只有空格 (<xref:System.ArgumentException> 類別)。  
  
-   路徑是唯讀的 (<xref:System.IO.IOException> 類別)。  
  
-   路徑名稱是 `Nothing` (<xref:System.ArgumentNullException> 類別)。  
  
-   路徑名稱過長 (<xref:System.IO.PathTooLongException> 類別)。  
  
-   路徑是無效的 (<xref:System.IO.DirectoryNotFoundException> 類別)。  
  
-   路徑只有一個冒號 ":" (<xref:System.NotSupportedException> 類別)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請勿根據檔案名稱來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [操作說明：播放 Windows Forms 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [SoundPlayer 類別概觀](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
