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
ms.openlocfilehash: f52cac4ca16adee232fae6fe2c1540bf5d3cb8cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708180"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="320c4-102">HOW TO：播放內嵌在 Windows Forms 資源中的音效</span><span class="sxs-lookup"><span data-stu-id="320c4-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="320c4-103">您可以使用<xref:System.Media.SoundPlayer>類別，以從內嵌資源播放音效。</span><span class="sxs-lookup"><span data-stu-id="320c4-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="320c4-104">範例</span><span class="sxs-lookup"><span data-stu-id="320c4-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="320c4-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="320c4-105">Compiling the Code</span></span>  
 <span data-ttu-id="320c4-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="320c4-106">This example requires:</span></span>  
  
 <span data-ttu-id="320c4-107">匯入<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="320c4-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="320c4-108">將音效檔包含為專案中的內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="320c4-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="320c4-109">將「\<組件名稱>」取代為內嵌音效檔的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="320c4-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="320c4-110">請不要包括 ".dll" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="320c4-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320c4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="320c4-111">See also</span></span>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="320c4-112">如何：從 Windows Form 播放的音效</span><span class="sxs-lookup"><span data-stu-id="320c4-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="320c4-113">如何：循環播放 Windows Form 上播放的音效</span><span class="sxs-lookup"><span data-stu-id="320c4-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
