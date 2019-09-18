---
title: 從應用程式定義域擷取安裝資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053109"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="44309-102">從應用程式定義域擷取安裝資訊</span><span class="sxs-lookup"><span data-stu-id="44309-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="44309-103">每個應用程式定義域的執行個體都包含這兩個屬性及 <xref:System.AppDomainSetup> 資訊。</span><span class="sxs-lookup"><span data-stu-id="44309-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="44309-104">您可以從使用 <xref:System.AppDomain?displayProperty=nameWithType> 類別的應用程式定義域擷取安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="44309-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="44309-105">這個類別提供數個成員，它們會擷取應用程式定義域的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="44309-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="44309-106">您也可以查詢應用程式定義域的 **AppDomainSetup** 物件，取得在建立時即已傳遞至定義域的安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="44309-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="44309-107">下例會建立新的應用程式定義域，然後將數個成員值列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="44309-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="44309-108">然後，下列範例集會擷取應用程式定義域的安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="44309-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="44309-109">請注意，`AppDomain.SetupInformation.ApplicationBase` 取得組態資訊。</span><span class="sxs-lookup"><span data-stu-id="44309-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="44309-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44309-110">See also</span></span>

- [<span data-ttu-id="44309-111">使用應用程式定義域設計程式</span><span class="sxs-lookup"><span data-stu-id="44309-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="44309-112">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="44309-112">Using Application Domains</span></span>](use.md)
