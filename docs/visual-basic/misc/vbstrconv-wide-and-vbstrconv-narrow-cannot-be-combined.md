---
title: 無法合併 VbStrConv.Wide 和 VbStrConv.Narrow
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: 7193d1f635ff877ab5d07f03584f19f5ce18138a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059364"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a><span data-ttu-id="9e664-102">無法合併 VbStrConv.Wide 和 VbStrConv.Narrow</span><span class="sxs-lookup"><span data-stu-id="9e664-102">VbStrConv.Wide and VbStrConv.Narrow cannot be combined</span></span>

<span data-ttu-id="9e664-103">您的應用程式嘗試合併 `VbStrConv` 列舉成員 `Wide` 和 `Narrow`，但它們互斥。</span><span class="sxs-lookup"><span data-stu-id="9e664-103">Your application is trying to combine the `VbStrConv` enumeration members `Wide` and `Narrow`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e664-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9e664-104">To correct this error</span></span>  
  
1. <span data-ttu-id="9e664-105">請移除 `VbStrConv.Wide` 或 `VbStrConv.Narrow`。</span><span class="sxs-lookup"><span data-stu-id="9e664-105">Remove either `VbStrConv.Wide` or `VbStrConv.Narrow`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e664-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e664-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="9e664-107">開發全球化和當地語系化應用程式</span><span class="sxs-lookup"><span data-stu-id="9e664-107">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
