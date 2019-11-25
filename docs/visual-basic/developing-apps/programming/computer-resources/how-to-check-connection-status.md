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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345886"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="1c265-102">如何：在 Visual Basic 中檢查連接狀態</span><span class="sxs-lookup"><span data-stu-id="1c265-102">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="1c265-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> 屬性可用來判斷電腦具有工作中的網路或網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="1c265-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="1c265-104">檢查電腦是否有工作中的連線</span><span class="sxs-lookup"><span data-stu-id="1c265-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="1c265-105">判斷 `IsAvailable` 屬性是 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="1c265-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="1c265-106">下列程式碼會檢查並報告屬性的狀態︰</span><span class="sxs-lookup"><span data-stu-id="1c265-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="1c265-107">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="1c265-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="1c265-108">在程式碼片段選擇器中，該程式碼片段會位於 [連接和網路] 中。</span><span class="sxs-lookup"><span data-stu-id="1c265-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="1c265-109">如需詳細資訊，請參閱 [Code Snippets](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="1c265-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c265-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c265-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
