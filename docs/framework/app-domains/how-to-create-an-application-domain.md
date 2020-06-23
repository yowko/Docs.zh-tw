---
title: 作法：建立應用程式定義域
description: 請參閱如何在 .NET 中建立應用程式域。 您可以建立應用程式域來載入元件以管理個人，或建立一個以執行程式碼。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104809"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="469c6-104">作法：建立應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="469c6-104">How to: Create an Application Domain</span></span>
<span data-ttu-id="469c6-105">Common Language Runtime Host 會在有需要時自動建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="469c6-105">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="469c6-106">不過，您可以建立自己的應用程式定義域，將它們載入您想要自行管理的組件中。</span><span class="sxs-lookup"><span data-stu-id="469c6-106">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="469c6-107">您也可以建立要從中執行程式碼的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="469c6-107">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="469c6-108">使用 <xref:System.AppDomain?displayProperty=nameWithType> 類別的其中一個多載 **CreateDomain** 方法，建立新的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="469c6-108">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="469c6-109">您可以提供應用程式定義域的名稱，並依該名稱參考它。</span><span class="sxs-lookup"><span data-stu-id="469c6-109">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="469c6-110">以下範例會建立新的應用程式定義域並指派名稱 `MyDomain`，然後將主機網域和新建子應用程式定義域的名稱列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="469c6-110">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="469c6-111">範例</span><span class="sxs-lookup"><span data-stu-id="469c6-111">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="469c6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="469c6-112">See also</span></span>

- [<span data-ttu-id="469c6-113">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="469c6-113">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="469c6-114">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="469c6-114">Using Application Domains</span></span>](use.md)
