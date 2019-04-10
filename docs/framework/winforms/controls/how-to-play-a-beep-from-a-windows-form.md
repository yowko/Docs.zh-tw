---
title: HOW TO：播放 Windows Forms 的嗶聲
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
ms.openlocfilehash: 0aa01f600873dd8853e1c33d5443448835e11455
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146220"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>HOW TO：播放 Windows Forms 的嗶聲
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
>  在中播放的音效C#程式碼範例由<xref:System.Media.SystemSounds.Beep%2A>系統音效設定。 如需詳細資訊，請參閱<xref:System.Media.SystemSounds>。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 針對C#，此範例需要參考<xref:System.Media?displayProperty=nameWithType>命名空間。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [HOW TO：播放 Windows Forms 的系統音效](how-to-play-a-system-sound-from-a-windows-form.md)
- [HOW TO：播放 Windows Forms 的音效](how-to-play-a-sound-from-a-windows-form.md)
