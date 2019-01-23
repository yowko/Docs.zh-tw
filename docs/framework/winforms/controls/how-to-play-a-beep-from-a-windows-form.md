---
title: HOW TO：從 Windows Form 播放嗶聲
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
ms.openlocfilehash: b847f2f759667eed5dfb6f9168a5c2fc50909cc3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544506"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="49728-102">HOW TO：從 Windows Form 播放嗶聲</span><span class="sxs-lookup"><span data-stu-id="49728-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="49728-103">這個範例會在執行階段播放嗶聲。</span><span class="sxs-lookup"><span data-stu-id="49728-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49728-104">範例</span><span class="sxs-lookup"><span data-stu-id="49728-104">Example</span></span>  
  
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
>  <span data-ttu-id="49728-105">在中播放的音效C#程式碼範例由<xref:System.Media.SystemSounds.Beep%2A>系統音效設定。</span><span class="sxs-lookup"><span data-stu-id="49728-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="49728-106">如需詳細資訊，請參閱<xref:System.Media.SystemSounds>。</span><span class="sxs-lookup"><span data-stu-id="49728-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49728-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="49728-107">Compiling the Code</span></span>  
 <span data-ttu-id="49728-108">針對C#，此範例需要參考<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="49728-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49728-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49728-109">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="49728-110">如何：從 Windows Form 播放系統音效</span><span class="sxs-lookup"><span data-stu-id="49728-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="49728-111">如何：從 Windows Form 播放的音效</span><span class="sxs-lookup"><span data-stu-id="49728-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
