---
title: 如何：使用反映取得類型和成員資訊
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130208"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="f7bd0-102">如何：使用反映取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="f7bd0-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="f7bd0-103"><xref:System.Reflection>命名空間包含許多方法，可取得類型及其成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="f7bd0-104">本文示範其中一種方法： <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7bd0-105">如需其他資訊，請參閱[反映總覽](reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="f7bd0-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="f7bd0-106">範例</span><span class="sxs-lookup"><span data-stu-id="f7bd0-106">Example</span></span>

<span data-ttu-id="f7bd0-107">下列範例會使用反映來取得型別和成員資訊：</span><span class="sxs-lookup"><span data-stu-id="f7bd0-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="f7bd0-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7bd0-108">See also</span></span>

- [<span data-ttu-id="f7bd0-109">使用應用程式域的程式</span><span class="sxs-lookup"><span data-stu-id="f7bd0-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="f7bd0-110">反射</span><span class="sxs-lookup"><span data-stu-id="f7bd0-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="f7bd0-111">使用應用程式域</span><span class="sxs-lookup"><span data-stu-id="f7bd0-111">Use application domains</span></span>](../app-domains/use.md)
