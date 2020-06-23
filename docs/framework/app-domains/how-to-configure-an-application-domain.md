---
title: 作法：設定應用程式定義域
description: 在 .NET 中設定應用程式域。 您可以使用 AppDomainSetup 類別，為 CLR 提供新應用程式域的設定資訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: 27afcf161bec74143fafb5dceb20597de73e23d4
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104863"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="4924c-104">作法：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="4924c-104">How to: Configure an Application Domain</span></span>
<span data-ttu-id="4924c-105">您可以使用 <xref:System.AppDomainSetup> 類別向 Common Language Runtime 提供新應用程式定義域的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="4924c-105">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="4924c-106">建立您自己的應用程式定義域時，最重要的屬性是 <xref:System.AppDomainSetup.ApplicationBase%2A>。</span><span class="sxs-lookup"><span data-stu-id="4924c-106">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="4924c-107">其他 **AppDomainSetup** 屬性主要是執行階段主機用來設定特定的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="4924c-107">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="4924c-108">**ApplicationBase** 屬性會定義應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="4924c-108">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="4924c-109">當執行階段需要滿足類型要求時，它會探查組件在 **ApplicationBase** 屬性指定的目錄中是否包含該類型。</span><span class="sxs-lookup"><span data-stu-id="4924c-109">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4924c-110">新的應用程式定義域只繼承建立者的 **ApplicationBase** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4924c-110">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="4924c-111">以下範例會建立 **AppDomainSetup** 類別的執行個體、使用此類別建立新的應用程式定義域、將資訊寫入主控台，再卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="4924c-111">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4924c-112">範例</span><span class="sxs-lookup"><span data-stu-id="4924c-112">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4924c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4924c-113">See also</span></span>

- [<span data-ttu-id="4924c-114">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="4924c-114">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="4924c-115">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="4924c-115">Using Application Domains</span></span>](use.md)
