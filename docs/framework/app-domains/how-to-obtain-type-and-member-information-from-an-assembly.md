---
title: 如何：從組件中取得類型和成員資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44fcded298f33a420a505900f618c1c67f4b9b6f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50180058"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="c429c-102">如何：從組件中取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="c429c-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="c429c-103"><xref:System.Reflection> 命名空間包含許多方法可以從組件中取得資訊。</span><span class="sxs-lookup"><span data-stu-id="c429c-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="c429c-104">本節示範其中一種方法。</span><span class="sxs-lookup"><span data-stu-id="c429c-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="c429c-105">如需詳細資訊，請參閱[反映概觀](../../../docs/framework/reflection-and-codedom/reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="c429c-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="c429c-106">下列範例會從組件中取得類型和成員資訊。</span><span class="sxs-lookup"><span data-stu-id="c429c-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c429c-107">範例</span><span class="sxs-lookup"><span data-stu-id="c429c-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="c429c-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="c429c-108">See Also</span></span>  
- [<span data-ttu-id="c429c-109">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="c429c-109">Programming with Application Domains</span></span>](./application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="c429c-110">反映</span><span class="sxs-lookup"><span data-stu-id="c429c-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
- [<span data-ttu-id="c429c-111">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="c429c-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
