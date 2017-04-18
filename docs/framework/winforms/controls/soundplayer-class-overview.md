---
title: "SoundPlayer 類別概觀 | Microsoft Docs"
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
  - "播放音效，SoundPlayer 類別"
  - "SoundPlayer 類別，關於 SoundPlayer 類別"
  - "播放音效"
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# SoundPlayer 類別概觀
<xref:System.Media.SoundPlayer>類別可讓您輕鬆地在應用程式中包含音效。  
  
 <xref:System.Media.SoundPlayer>類別可以播放.wav 格式，從資源，或是從 UNC 或 HTTP 位置中的音效檔。 此外， <xref:System.Media.SoundPlayer>類別可讓您載入或以非同步方式播放音效。  
  
 您也可以使用<xref:System.Media.SystemSounds>類別來播放常見的系統音效，包括嗶聲。  
  
## <a name="commonly-used-properties-methods-and-events"></a>常用的屬性、 方法和事件  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A>屬性|檔案路徑或網址的聲音。 可接受的值可以是 UNC 或 HTTP。|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A>屬性|您的程式會載入音效之前等候的毫秒數，會擲回例外狀況。 預設為 10 秒。|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A>屬性|布林值，指出是否將聲音完成載入。|  
|<xref:System.Media.SoundPlayer.Load%2A>方法|以同步方式載入音效。|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A>方法|開始非同步載入音效。 載入完成時，便會產生<xref:System.Media.SoundPlayer.OnLoadCompleted%2A>事件。|  
|<xref:System.Media.SoundPlayer.Play%2A>方法|指定在播放<xref:System.Media.SoundPlayer.SoundLocation%2A>或<xref:System.Media.SoundPlayer.Stream%2A>中新的執行緒屬性。|  
|<xref:System.Media.SoundPlayer.PlaySync%2A>方法|指定在播放<xref:System.Media.SoundPlayer.SoundLocation%2A>或<xref:System.Media.SoundPlayer.Stream%2A>目前執行緒中的屬性。|  
|<xref:System.Media.SoundPlayer.Stop%2A>方法|停止目前正在播放任何聲音。|  
|<xref:System.Media.SoundPlayer.LoadCompleted>事件|嘗試載入音效之後引發。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer>   
 <xref:System.Media.SystemSounds>