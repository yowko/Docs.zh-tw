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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078573"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>HOW TO：播放內嵌在 Windows Forms 資源中的音效
您可以使用<xref:System.Media.SoundPlayer>類別，以從內嵌資源播放音效。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
 匯入<xref:System.Media?displayProperty=nameWithType>命名空間。  
  
 將音效檔包含為專案中的內嵌資源。  
  
 將「\<組件名稱>」取代為內嵌音效檔的組件名稱。 請不要包括 ".dll" 尾碼。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Media.SoundPlayer>
- [如何：從 Windows Form 播放的音效](how-to-play-a-sound-from-a-windows-form.md)
- [如何：循環播放 Windows Form 上播放的音效](how-to-loop-a-sound-playing-on-a-windows-form.md)
