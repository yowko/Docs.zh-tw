---
title: 如何：設定應用程式定義域
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8db75edec8e80e0e137593a424f12575cfc747b
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="2cefb-102">如何：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="2cefb-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="2cefb-103">您可以使用 <xref:System.AppDomainSetup> 類別向 Common Language Runtime 提供新應用程式定義域的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="2cefb-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="2cefb-104">建立您自己的應用程式定義域時，最重要的屬性是 <xref:System.AppDomainSetup.ApplicationBase%2A>。</span><span class="sxs-lookup"><span data-stu-id="2cefb-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="2cefb-105">其他 **AppDomainSetup** 屬性主要是執行階段主機用來設定特定的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="2cefb-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="2cefb-106">**ApplicationBase** 屬性會定義應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="2cefb-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="2cefb-107">當執行階段需要滿足類型要求時，它會探查組件在 **ApplicationBase** 屬性指定的目錄中是否包含該類型。</span><span class="sxs-lookup"><span data-stu-id="2cefb-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cefb-108">新的應用程式定義域只繼承建立者的 **ApplicationBase** 屬性。</span><span class="sxs-lookup"><span data-stu-id="2cefb-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="2cefb-109">以下範例會建立 **AppDomainSetup** 類別的執行個體、使用此類別建立新的應用程式定義域、將資訊寫入主控台，再卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="2cefb-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cefb-110">範例</span><span class="sxs-lookup"><span data-stu-id="2cefb-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2cefb-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="2cefb-111">See Also</span></span>  
 [<span data-ttu-id="2cefb-112">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="2cefb-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="2cefb-113">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="2cefb-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
