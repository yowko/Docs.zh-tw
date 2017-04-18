---
title: "如何：播放內嵌在 Windows Form 資源中的音效 | Microsoft Docs"
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
  - "從資源播放音效"
  - "播放音效的資源 [Windows Form]"
  - "播放資源中的音效"
  - "SoundPlayer 類別，播放資源中的音效"
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：播放內嵌在 Windows Form 資源中的音效
您可以使用<xref:System.Media.SoundPlayer>類別，以從內嵌資源播放音效。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
 匯入<xref:System.Media?displayProperty=fullName>命名空間。  
  
 為您的專案中的內嵌資源包含音效檔。  
  
 取代 「<>\>"內嵌音效檔所在的組件的名稱。 不包含".dll"後置字元。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer>   
 [如何︰ 播放 Windows Form 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)   
 [如何︰ 循環播放 Windows Form 上的音效](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)