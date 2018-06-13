---
title: 如何：播放 Windows Form 中的系統音效
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
ms.openlocfilehash: 4dfda2b6d73e346d85690f66a3e92858381ae7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532395"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>如何：播放 Windows Form 中的系統音效
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
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>  
 [操作說明：播放 Windows Forms 中的嗶聲](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 [操作說明：播放 Windows Forms 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
