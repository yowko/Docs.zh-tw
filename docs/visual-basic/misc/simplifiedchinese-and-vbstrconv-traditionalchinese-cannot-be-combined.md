---
title: 無法合併 SimplifiedChinese 和 VbStrConv.TraditionalChinese
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_StrConvSCandTC
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
ms.openlocfilehash: 512651add89de23b35512e736dbf74f0891c995a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91060480"
---
# <a name="simplifiedchinese-and-vbstrconvtraditionalchinese-cannot-be-combined"></a><span data-ttu-id="10606-102">無法合併 SimplifiedChinese 和 VbStrConv.TraditionalChinese</span><span class="sxs-lookup"><span data-stu-id="10606-102">SimplifiedChinese and VbStrConv.TraditionalChinese cannot be combined</span></span>

<span data-ttu-id="10606-103">您的應用程式嘗試合併 `VbStrConv` 列舉成員 `SimplifiedChinese` 和 `TraditionalChinese`，但它們互斥。</span><span class="sxs-lookup"><span data-stu-id="10606-103">Your application is attempting to combine the `VbStrConv` enumeration members `SimplifiedChinese` and `TraditionalChinese`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10606-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="10606-104">To correct this error</span></span>  
  
- <span data-ttu-id="10606-105">請移除 `VbStrConv.SimplifiedChinese` 或 `VbStrConv.TraditionalChinese`。</span><span class="sxs-lookup"><span data-stu-id="10606-105">Remove either `VbStrConv.SimplifiedChinese` or `VbStrConv.TraditionalChinese`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10606-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10606-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="10606-107">開發全球化和當地語系化應用程式</span><span class="sxs-lookup"><span data-stu-id="10606-107">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
