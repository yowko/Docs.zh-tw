---
title: HOW TO：播放 Windows Forms 的系統音效
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
ms.openlocfilehash: d85d8cd40ff2b32cb3f2a79cf9a8221964f186c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913285"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="78a72-102">HOW TO：播放 Windows Forms 的系統音效</span><span class="sxs-lookup"><span data-stu-id="78a72-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="78a72-103">下列程式碼範例會在執行階段播放 `Exclamation` 系統音效。</span><span class="sxs-lookup"><span data-stu-id="78a72-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="78a72-104">如需系統音效的詳細資訊，請參閱<xref:System.Media.SystemSounds>。</span><span class="sxs-lookup"><span data-stu-id="78a72-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a72-105">範例</span><span class="sxs-lookup"><span data-stu-id="78a72-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="78a72-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="78a72-106">Compiling the Code</span></span>  
 <span data-ttu-id="78a72-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="78a72-107">This example requires:</span></span>  
  
-   <span data-ttu-id="78a72-108"><xref:System.Media?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="78a72-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a72-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78a72-109">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [<span data-ttu-id="78a72-110">如何：從 Windows Form 播放嗶聲</span><span class="sxs-lookup"><span data-stu-id="78a72-110">How to: Play a Beep from a Windows Form</span></span>](how-to-play-a-beep-from-a-windows-form.md)
- [<span data-ttu-id="78a72-111">如何：從 Windows Form 播放的音效</span><span class="sxs-lookup"><span data-stu-id="78a72-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
