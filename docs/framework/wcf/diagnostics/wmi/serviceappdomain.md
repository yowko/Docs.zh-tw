---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d948d1c77fc3f188694062ca9dcb3058f408c45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="4a8a1-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="4a8a1-102">ServiceAppDomain</span></span>
<span data-ttu-id="4a8a1-103">將服務對應至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="4a8a1-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a8a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a8a1-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4a8a1-105">方法</span><span class="sxs-lookup"><span data-stu-id="4a8a1-105">Methods</span></span>  
 <span data-ttu-id="4a8a1-106">ServiceAppDomain 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="4a8a1-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a8a1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4a8a1-107">Properties</span></span>  
 <span data-ttu-id="4a8a1-108">ServiceAppDomain 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4a8a1-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="4a8a1-109">ref</span><span class="sxs-lookup"><span data-stu-id="4a8a1-109">ref</span></span>  
 <span data-ttu-id="4a8a1-110">資料型別：服務</span><span class="sxs-lookup"><span data-stu-id="4a8a1-110">Data type: Service</span></span>  
<span data-ttu-id="4a8a1-111">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="4a8a1-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="4a8a1-112">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4a8a1-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a8a1-113">這個應用程式定義域的服務。</span><span class="sxs-lookup"><span data-stu-id="4a8a1-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="4a8a1-114">ref</span><span class="sxs-lookup"><span data-stu-id="4a8a1-114">ref</span></span>  
 <span data-ttu-id="4a8a1-115">資料型別：AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="4a8a1-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="4a8a1-116">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="4a8a1-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="4a8a1-117">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4a8a1-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a8a1-118">包含應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a8a1-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a8a1-119">需求</span><span class="sxs-lookup"><span data-stu-id="4a8a1-119">Requirements</span></span>  
  
|<span data-ttu-id="4a8a1-120">MOF</span><span class="sxs-lookup"><span data-stu-id="4a8a1-120">MOF</span></span>|<span data-ttu-id="4a8a1-121">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="4a8a1-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4a8a1-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="4a8a1-122">Namespace</span></span>|<span data-ttu-id="4a8a1-123">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="4a8a1-123">Defined in root\ServiceModel</span></span>|
