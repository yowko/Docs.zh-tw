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
ms.locfileid: "33531210"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="bd264-102">如何：播放 Windows Form 中的嗶聲</span><span class="sxs-lookup"><span data-stu-id="bd264-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="bd264-103">這個範例會在執行階段播放嗶聲。</span><span class="sxs-lookup"><span data-stu-id="bd264-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd264-104">範例</span><span class="sxs-lookup"><span data-stu-id="bd264-104">Example</span></span>  
  
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
>  <span data-ttu-id="bd264-105">在 C# 程式碼範例中播放的聲音由<xref:System.Media.SystemSounds.Beep%2A>系統音效的設定。</span><span class="sxs-lookup"><span data-stu-id="bd264-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="bd264-106">如需詳細資訊，請參閱<xref:System.Media.SystemSounds>。</span><span class="sxs-lookup"><span data-stu-id="bd264-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd264-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bd264-107">Compiling the Code</span></span>  
 <span data-ttu-id="bd264-108">C# 中，這個範例需要參考<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="bd264-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd264-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd264-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="bd264-110">操作說明：播放 Windows Forms 中的系統音效</span><span class="sxs-lookup"><span data-stu-id="bd264-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [<span data-ttu-id="bd264-111">操作說明：播放 Windows Forms 中的音效</span><span class="sxs-lookup"><span data-stu-id="bd264-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
