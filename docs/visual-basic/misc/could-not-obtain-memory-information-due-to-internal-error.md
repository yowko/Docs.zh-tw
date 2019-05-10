---
title: 由於內部錯誤，無法取得記憶體資訊
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: a59c815e0135f02f06ae9d4b7e2c21468af1ba03
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598371"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="78b4a-102">由於內部錯誤，無法取得記憶體資訊</span><span class="sxs-lookup"><span data-stu-id="78b4a-102">Could not obtain memory information due to internal error</span></span>
<span data-ttu-id="78b4a-103">呼叫 `My.Computer.Info` 物件的其中一個記憶體資訊屬性失敗。</span><span class="sxs-lookup"><span data-stu-id="78b4a-103">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78b4a-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="78b4a-104">To correct this error</span></span>  
  
- <span data-ttu-id="78b4a-105">在 `Try...Catch` 物件之記憶體資訊屬性的呼叫周圍加入 `My.Computer.Info` 區塊。</span><span class="sxs-lookup"><span data-stu-id="78b4a-105">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b4a-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78b4a-106">See also</span></span>

- [<span data-ttu-id="78b4a-107">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="78b4a-107">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [<span data-ttu-id="78b4a-108">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="78b4a-108">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
