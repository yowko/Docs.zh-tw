---
title: "如何：播放 Windows Form 中的音效 | Microsoft Docs"
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
  - "播放音效，Windows Form"
  - "播放音效"
  - "SoundPlayer 類別"
  - "音效"
  - "My.Computer.Audio 物件，並播放音效"
  - "範例 [Windows Form] 音效"
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：播放 Windows Form 中的音效
這個範例會在執行階段在指定的路徑播放音效。  
  
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
  
-   您將檔案名稱 `"c:\Windows\Media\chimes.wav"` 取代為有效的檔案名稱。  
  
-   (C#)參考<xref:System.Media?displayProperty=fullName>命名空間。  
  
## <a name="robust-programming"></a>穩固程式設計  
 檔案作業應含括在適當的結構化例外處理區塊內。  
  
 以下條件可能會造成例外狀況：  
  
-   路徑名稱的格式不正確。 例如，包含不合法的字元，或只有空格 (<xref:System.ArgumentException>類別)。  
  
-   路徑是唯讀的 (<xref:System.IO.IOException>類別)。  
  
-   路徑名稱是`null`(<xref:System.ArgumentNullException>類別)。  
  
-   路徑名稱過長 (<xref:System.IO.PathTooLongException>類別)。  
  
-   路徑無效 (<xref:System.IO.DirectoryNotFoundException>類別)。  
  
-   路徑是只有一個冒號":"(<xref:System.NotSupportedException>類別)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請勿根據檔案名稱來判斷檔案內容。 例如，`Form1.vb` 檔案可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer>   
 [如何︰ 在 Windows Form 中的非同步載入音效](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)   
 