---
title: "如何：播放 Windows Form 中的系統音效 | Microsoft Docs"
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
  - "針對系統事件播放音效"
  - "播放音效，Windows Form"
  - "系統音效，從 Windows Form 播放"
  - "播放音效，系統"
  - "SoundPlayer 類別，系統音效"
  - "播放音效"
  - "範例 [Windows Form] 音效"
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：播放 Windows Form 中的系統音效
下列程式碼範例中所扮演`Exclamation`在執行階段的系統音效。 如需系統音效，請參閱<xref:System.Media.SystemSounds>。  
  
## <a name="example"></a>範例  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   參考<xref:System.Media?displayProperty=fullName>命名空間。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer>   
 <xref:System.Media.SystemSounds>   
 [如何︰ 播放 Windows Form 中的嗶聲](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)   
 [如何︰ 播放 Windows Form 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)