---
title: 無法合併 VbStrConv.Wide 和 VbStrConv.Narrow
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: 917fcdfcb34778074db6a19c04e12c3cf8de90dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307921"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a><span data-ttu-id="ef8be-102">無法合併 VbStrConv.Wide 和 VbStrConv.Narrow</span><span class="sxs-lookup"><span data-stu-id="ef8be-102">VbStrConv.Wide and VbStrConv.Narrow cannot be combined</span></span>
<span data-ttu-id="ef8be-103">您的應用程式嘗試合併 `VbStrConv` 列舉成員 `Wide` 和 `Narrow`，但它們互斥。</span><span class="sxs-lookup"><span data-stu-id="ef8be-103">Your application is trying to combine the `VbStrConv` enumeration members `Wide` and `Narrow`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef8be-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ef8be-104">To correct this error</span></span>  
  
1. <span data-ttu-id="ef8be-105">請移除 `VbStrConv.Wide` 或 `VbStrConv.Narrow`。</span><span class="sxs-lookup"><span data-stu-id="ef8be-105">Remove either `VbStrConv.Wide` or `VbStrConv.Narrow`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8be-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef8be-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="ef8be-107">以 .NET Framework 為基礎的國際應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="ef8be-107">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
