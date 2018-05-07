---
title: 如何：播放 Windows Form 中的嗶聲
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
ms.openlocfilehash: 460309d853f2b3b423d14a820771e0230358e3c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>如何：播放 Windows Form 中的嗶聲
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
>  在 C# 程式碼範例中播放的聲音由<xref:System.Media.SystemSounds.Beep%2A>系統音效的設定。 如需詳細資訊，請參閱<xref:System.Media.SystemSounds>。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 C# 中，這個範例需要參考<xref:System.Media?displayProperty=nameWithType>命名空間。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [操作說明：播放 Windows Forms 中的系統音效](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [操作說明：播放 Windows Forms 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
