---
title: "如何：在 Windows Form 中非同步地載入音效 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "SoundPlayer 類別，以非同步方式載入音效"
  - "在個別執行緒上載入音效"
  - "執行緒處理 [Windows Form]，聽起來"
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：在 Windows Form 中非同步地載入音效
下列程式碼範例會以非同步方式從 URL 載入音效，然後在新的執行緒上播放。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   本系統和 System.Windows.Forms 組件的參考。  
  
-   您將檔案名稱 `"http://www.tailspintoys.com/sounds/stop.wav"` 取代為有效的檔案名稱。  
  
 如需有關建置這個範例，從命令列資訊[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]或[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)或[使用 csc.exe 建置](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[How to︰ 編譯並執行完整 Windows Form 程式碼範例使用 Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="robust-programming"></a>穩固程式設計  
 檔案作業應含括在適當的例外狀況處理區塊內。  
  
 以下條件可能會造成例外狀況：  
  
-   路徑名稱的格式不正確。 例如，包含無效的字元，或只有空格 (<xref:System.ArgumentException>類別)。  
  
-   路徑是唯讀的 (<xref:System.IO.IOException>類別)。  
  
-   路徑名稱是`Nothing`(<xref:System.ArgumentNullException>類別)。  
  
-   路徑名稱過長 (<xref:System.IO.PathTooLongException>類別)。  
  
-   路徑不正確 (<xref:System.IO.DirectoryNotFoundException>類別)。  
  
-   路徑是只有一個冒號":"(<xref:System.NotSupportedException>類別)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請勿根據檔案名稱來判斷檔案內容。 例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>   
 <xref:System.Media.SoundPlayer.LoadCompleted>   
 <xref:System.Media.SoundPlayer.Play%2A>   
 [如何︰ 播放 Windows Form 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)