---
title: "如何：播放 Windows Form 中的嗶聲 | Microsoft Docs"
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
  - "音效、 嗶聲"
  - "Windows Form、 音效"
  - "播放音效"
  - "表單、 音效"
  - "範例 [Windows Form] 音效"
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：播放 Windows Form 中的嗶聲
此範例會播放嗶聲，在執行階段。  
  
## <a name="example"></a>範例  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  在 C# 程式碼範例中播放的聲音由<xref:System.Media.SystemSounds.Beep%2A>系統音效設定。 如需詳細資訊，請參閱<xref:System.Media.SystemSounds>。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 C# 中，這個範例需要參考<xref:System.Media?displayProperty=fullName>命名空間。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>   
 <xref:System.Media.SoundPlayer>   
 [如何︰ 播放 Windows Form 中的系統音效](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)   
 [如何︰ 播放 Windows Form 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)