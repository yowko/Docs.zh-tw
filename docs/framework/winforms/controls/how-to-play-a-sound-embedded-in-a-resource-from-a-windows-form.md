---
title: 如何：播放內嵌在 Windows Form 資源中的音效
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
ms.openlocfilehash: c9dc8499e2d12ed17f9b409a805148d08da894fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>如何：播放內嵌在 Windows Form 資源中的音效
您可以使用<xref:System.Media.SoundPlayer>類別，以從內嵌資源播放音效。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
 匯入<xref:System.Media?displayProperty=nameWithType>命名空間。  
  
 將音效檔包含為專案中的內嵌資源。  
  
 將「\<組件名稱>」取代為內嵌音效檔的組件名稱。 請不要包括 ".dll" 尾碼。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Media.SoundPlayer>  
 [操作說明：播放 Windows Forms 中的音效](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [操作說明：在 Windows Forms 上循環播放音效](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
