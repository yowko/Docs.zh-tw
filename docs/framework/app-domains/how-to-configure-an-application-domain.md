---
title: HOW TO：設定應用程式定義域
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
ms.openlocfilehash: 8989d7695f44b0cd2e8b0ce3ec8bd74a6e802102
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534562"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="279f9-102">HOW TO：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="279f9-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="279f9-103">您可以使用 <xref:System.AppDomainSetup> 類別向 Common Language Runtime 提供新應用程式定義域的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="279f9-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="279f9-104">建立您自己的應用程式定義域時，最重要的屬性是 <xref:System.AppDomainSetup.ApplicationBase%2A>。</span><span class="sxs-lookup"><span data-stu-id="279f9-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="279f9-105">其他 **AppDomainSetup** 屬性主要是執行階段主機用來設定特定的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="279f9-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="279f9-106">**ApplicationBase** 屬性會定義應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="279f9-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="279f9-107">當執行階段需要滿足類型要求時，它會探查組件在 **ApplicationBase** 屬性指定的目錄中是否包含該類型。</span><span class="sxs-lookup"><span data-stu-id="279f9-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="279f9-108">新的應用程式定義域只繼承建立者的 **ApplicationBase** 屬性。</span><span class="sxs-lookup"><span data-stu-id="279f9-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="279f9-109">以下範例會建立 **AppDomainSetup** 類別的執行個體、使用此類別建立新的應用程式定義域、將資訊寫入主控台，再卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="279f9-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="279f9-110">範例</span><span class="sxs-lookup"><span data-stu-id="279f9-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="279f9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="279f9-111">See also</span></span>
- [<span data-ttu-id="279f9-112">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="279f9-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="279f9-113">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="279f9-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
