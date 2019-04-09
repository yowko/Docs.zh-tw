---
title: HOW TO：播放內嵌在 Windows Forms 資源中的音效
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078573"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="fc4ab-102">HOW TO：播放內嵌在 Windows Forms 資源中的音效</span><span class="sxs-lookup"><span data-stu-id="fc4ab-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="fc4ab-103">您可以使用<xref:System.Media.SoundPlayer>類別，以從內嵌資源播放音效。</span><span class="sxs-lookup"><span data-stu-id="fc4ab-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc4ab-104">範例</span><span class="sxs-lookup"><span data-stu-id="fc4ab-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc4ab-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fc4ab-105">Compiling the Code</span></span>  
 <span data-ttu-id="fc4ab-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="fc4ab-106">This example requires:</span></span>  
  
 <span data-ttu-id="fc4ab-107">匯入<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="fc4ab-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="fc4ab-108">將音效檔包含為專案中的內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="fc4ab-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="fc4ab-109">將「\<組件名稱>」取代為內嵌音效檔的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="fc4ab-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="fc4ab-110">請不要包括 ".dll" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="fc4ab-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4ab-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc4ab-111">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="fc4ab-112">HOW TO：播放 Windows Forms 的音效</span><span class="sxs-lookup"><span data-stu-id="fc4ab-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="fc4ab-113">HOW TO：循環播放 Windows Forms 的音效</span><span class="sxs-lookup"><span data-stu-id="fc4ab-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
