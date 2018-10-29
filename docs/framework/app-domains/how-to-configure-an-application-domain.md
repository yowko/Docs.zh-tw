---
title: 如何：設定應用程式定義域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 012f0220afa0e444d68af5998fb2492a03a371d8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50183161"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="dd5a5-102">如何：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="dd5a5-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="dd5a5-103">您可以使用 <xref:System.AppDomainSetup> 類別向 Common Language Runtime 提供新應用程式定義域的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="dd5a5-104">建立您自己的應用程式定義域時，最重要的屬性是 <xref:System.AppDomainSetup.ApplicationBase%2A>。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="dd5a5-105">其他 **AppDomainSetup** 屬性主要是執行階段主機用來設定特定的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="dd5a5-106">**ApplicationBase** 屬性會定義應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="dd5a5-107">當執行階段需要滿足類型要求時，它會探查組件在 **ApplicationBase** 屬性指定的目錄中是否包含該類型。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd5a5-108">新的應用程式定義域只繼承建立者的 **ApplicationBase** 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="dd5a5-109">以下範例會建立 **AppDomainSetup** 類別的執行個體、使用此類別建立新的應用程式定義域、將資訊寫入主控台，再卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="dd5a5-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd5a5-110">範例</span><span class="sxs-lookup"><span data-stu-id="dd5a5-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dd5a5-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5a5-111">See Also</span></span>  
- [<span data-ttu-id="dd5a5-112">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="dd5a5-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
- [<span data-ttu-id="dd5a5-113">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="dd5a5-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
