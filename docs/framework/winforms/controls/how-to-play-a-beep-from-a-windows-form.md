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
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="2ccf7-102">HOW TO：播放 Windows Forms 的嗶聲</span><span class="sxs-lookup"><span data-stu-id="2ccf7-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="2ccf7-103">這個範例會在執行階段播放嗶聲。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ccf7-104">範例</span><span class="sxs-lookup"><span data-stu-id="2ccf7-104">Example</span></span>  
  
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
>  <span data-ttu-id="2ccf7-105">在中播放的音效C#程式碼範例由<xref:System.Media.SystemSounds.Beep%2A>系統音效設定。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="2ccf7-106">如需詳細資訊，請參閱<xref:System.Media.SystemSounds>。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ccf7-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2ccf7-107">Compiling the Code</span></span>  
 <span data-ttu-id="2ccf7-108">針對C#，此範例需要參考<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ccf7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ccf7-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="2ccf7-110">HOW TO：播放 Windows Forms 的系統音效</span><span class="sxs-lookup"><span data-stu-id="2ccf7-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="2ccf7-111">HOW TO：播放 Windows Forms 的音效</span><span class="sxs-lookup"><span data-stu-id="2ccf7-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
