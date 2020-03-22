---
title: 如何：檢查連接狀態
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 89ef431759dac25bd213fd954db0712ad95434b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345886"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a>如何：在 Visual Basic 中檢查連接狀態

<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> 屬性可用來判斷電腦具有工作中的網路或網際網路連線。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>檢查電腦是否有工作中的連線  
  
- 判斷 `IsAvailable` 屬性是 `True` 或 `False`。 下列程式碼會檢查並報告屬性的狀態︰  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。**** 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
