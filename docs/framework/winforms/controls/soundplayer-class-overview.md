---
title: SoundPlayer 類別概觀
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195003"
---
# <a name="soundplayer-class-overview"></a>SoundPlayer 類別概觀
<xref:System.Media.SoundPlayer> 類別可讓您輕鬆地在應用程式中包含音效。  
  
 <xref:System.Media.SoundPlayer>類別可以播放.wav 格式，從資源或者從 UNC 或 HTTP 位置中的音效檔。 此外，<xref:System.Media.SoundPlayer>類別可讓您載入或以非同步方式播放音效。  
  
 您也可以使用 <xref:System.Media.SystemSounds> 類別來播放常見的系統音效，包括嗶聲。  
  
## <a name="commonly-used-properties-methods-and-events"></a>常用屬性、方法和事件  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> 屬性|音效的檔案路徑或網址。 可接受的值可以是 UNC 或 HTTP。|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> 屬性|程式在擲回例外狀況之前等待載入音效的毫秒數。 預設為 10 秒。|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> 屬性|表示音效是否完成載入的布林值。|  
|<xref:System.Media.SoundPlayer.Load%2A> 方法|同步載入音效。|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> 方法|開始非同步載入音效。 載入完成時，便會產生<xref:System.Media.SoundPlayer.OnLoadCompleted%2A>事件。|  
|<xref:System.Media.SoundPlayer.Play%2A> 方法|扮演指定的音效<xref:System.Media.SoundPlayer.SoundLocation%2A>或<xref:System.Media.SoundPlayer.Stream%2A>中新的執行緒屬性。|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> 方法|扮演指定的音效<xref:System.Media.SoundPlayer.SoundLocation%2A>或<xref:System.Media.SoundPlayer.Stream%2A>目前執行緒中的屬性。|  
|<xref:System.Media.SoundPlayer.Stop%2A> 方法|停止任何目前正在播放的音效。|  
|<xref:System.Media.SoundPlayer.LoadCompleted> 事件|在嘗試載入音效之後引發。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
