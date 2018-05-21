---
title: 如何：建立應用程式定義域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c579c97e273e7d3e149e04f7aa7670313663b617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="27f91-102">如何：建立應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="27f91-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="27f91-103">Common Language Runtime Host 會在有需要時自動建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="27f91-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="27f91-104">不過，您可以建立自己的應用程式定義域，將它們載入您想要自行管理的組件中。</span><span class="sxs-lookup"><span data-stu-id="27f91-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="27f91-105">您也可以建立要從中執行程式碼的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="27f91-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="27f91-106">使用 <xref:System.AppDomain?displayProperty=nameWithType> 類別的其中一個多載 **CreateDomain** 方法，建立新的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="27f91-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="27f91-107">您可以提供應用程式定義域的名稱，並依該名稱參考它。</span><span class="sxs-lookup"><span data-stu-id="27f91-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="27f91-108">以下範例會建立新的應用程式定義域並指派名稱 `MyDomain`，然後將主機網域和新建子應用程式定義域的名稱列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="27f91-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27f91-109">範例</span><span class="sxs-lookup"><span data-stu-id="27f91-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="27f91-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="27f91-110">See Also</span></span>  
 [<span data-ttu-id="27f91-111">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="27f91-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="27f91-112">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="27f91-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
