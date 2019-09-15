---
title: 作法：使用反映取得類型和成員資訊
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972918"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="59d7a-102">HOW TO：使用反映取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="59d7a-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="59d7a-103"><xref:System.Reflection>命名空間包含許多方法，可取得類型及其成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="59d7a-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="59d7a-104">本文示範其中一種方法： <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="59d7a-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="59d7a-105">如需其他資訊，請參閱[反映總覽](reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="59d7a-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="59d7a-106">範例</span><span class="sxs-lookup"><span data-stu-id="59d7a-106">Example</span></span>

<span data-ttu-id="59d7a-107">下列範例會使用反映來取得型別和成員資訊：</span><span class="sxs-lookup"><span data-stu-id="59d7a-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="59d7a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59d7a-108">See also</span></span>

- [<span data-ttu-id="59d7a-109">使用應用程式域的程式</span><span class="sxs-lookup"><span data-stu-id="59d7a-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="59d7a-110">反映</span><span class="sxs-lookup"><span data-stu-id="59d7a-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="59d7a-111">使用應用程式域</span><span class="sxs-lookup"><span data-stu-id="59d7a-111">Use application domains</span></span>](../app-domains/use.md)
