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
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="988ed-102">作法：播放 Windows Forms 的嗶聲</span><span class="sxs-lookup"><span data-stu-id="988ed-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="988ed-103">這個範例會在執行階段播放嗶聲。</span><span class="sxs-lookup"><span data-stu-id="988ed-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="988ed-104">範例</span><span class="sxs-lookup"><span data-stu-id="988ed-104">Example</span></span>  
  
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
> <span data-ttu-id="988ed-105">在程式C#代碼範例中播放的聲音是由<xref:System.Media.SystemSounds.Beep%2A>系統音效設定所決定。</span><span class="sxs-lookup"><span data-stu-id="988ed-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="988ed-106">如需詳細資訊，請參閱 <xref:System.Media.SystemSounds>。</span><span class="sxs-lookup"><span data-stu-id="988ed-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="988ed-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="988ed-107">Compiling the Code</span></span>  
 <span data-ttu-id="988ed-108">針對C#, 此範例需要<xref:System.Media?displayProperty=nameWithType>命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="988ed-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988ed-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="988ed-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="988ed-110">如何：播放 Windows Form 中的系統音效</span><span class="sxs-lookup"><span data-stu-id="988ed-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="988ed-111">如何：播放 Windows Form 中的音效</span><span class="sxs-lookup"><span data-stu-id="988ed-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
