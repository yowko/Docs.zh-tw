---
title: HOW TO：從 Windows Form 播放系統音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: 1883e73f3b1937e8568b751d1cb9f3b57548c010
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649501"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>HOW TO：從 Windows Form 播放系統音效
下列程式碼範例會在執行階段播放 `Exclamation` 系統音效。 如需系統音效的詳細資訊，請參閱<xref:System.Media.SystemSounds>。  
  
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
  
-   <xref:System.Media?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [如何：從 Windows Form 播放嗶聲](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)
- [如何：從 Windows Form 播放的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
