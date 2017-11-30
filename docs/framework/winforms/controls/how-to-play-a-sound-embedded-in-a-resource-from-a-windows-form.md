---
title: "如何：播放內嵌在 Windows Form 資源中的音效"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 82e143a6c405d4f3065c18a1a118891e0e692b93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="35dc8-102">如何：播放內嵌在 Windows Form 資源中的音效</span><span class="sxs-lookup"><span data-stu-id="35dc8-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="35dc8-103">您可以使用<xref:System.Media.SoundPlayer>類別，以從內嵌資源播放音效。</span><span class="sxs-lookup"><span data-stu-id="35dc8-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35dc8-104">範例</span><span class="sxs-lookup"><span data-stu-id="35dc8-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35dc8-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="35dc8-105">Compiling the Code</span></span>  
 <span data-ttu-id="35dc8-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="35dc8-106">This example requires:</span></span>  
  
 <span data-ttu-id="35dc8-107">匯入<xref:System.Media?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="35dc8-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="35dc8-108">將音效檔包含為專案中的內嵌資源。</span><span class="sxs-lookup"><span data-stu-id="35dc8-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="35dc8-109">將「\<組件名稱>」取代為內嵌音效檔的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="35dc8-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="35dc8-110">請不要包括 ".dll" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="35dc8-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35dc8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35dc8-111">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="35dc8-112">操作說明：播放 Windows Forms 中的音效</span><span class="sxs-lookup"><span data-stu-id="35dc8-112">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="35dc8-113">操作說明：在 Windows Forms 上循環播放音效</span><span class="sxs-lookup"><span data-stu-id="35dc8-113">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
