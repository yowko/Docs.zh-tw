---
title: 作法：播放 Windows Forms 的嗶聲
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: 1a72f88c05fb21c11864058ffbe81c1957525375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966514"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>作法：播放 Windows Forms 的嗶聲
這個範例會在執行階段播放嗶聲。  
  
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
> 在程式C#代碼範例中播放的聲音是由<xref:System.Media.SystemSounds.Beep%2A>系統音效設定所決定。 如需詳細資訊，請參閱 <xref:System.Media.SystemSounds>。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 針對C#, 此範例需要<xref:System.Media?displayProperty=nameWithType>命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [如何：播放 Windows Form 中的系統音效](how-to-play-a-system-sound-from-a-windows-form.md)
- [如何：播放 Windows Form 中的音效](how-to-play-a-sound-from-a-windows-form.md)
