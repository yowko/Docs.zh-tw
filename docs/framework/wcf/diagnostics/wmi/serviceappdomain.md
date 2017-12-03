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
ms.openlocfilehash: 325497435e24843cc74e804ef38e562617f27167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="a8097-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="a8097-102">ServiceAppDomain</span></span>
<span data-ttu-id="a8097-103">將服務對應至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a8097-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8097-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8097-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a8097-105">方法</span><span class="sxs-lookup"><span data-stu-id="a8097-105">Methods</span></span>  
 <span data-ttu-id="a8097-106">ServiceAppDomain 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a8097-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a8097-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a8097-107">Properties</span></span>  
 <span data-ttu-id="a8097-108">ServiceAppDomain 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a8097-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a8097-109">ref</span><span class="sxs-lookup"><span data-stu-id="a8097-109">ref</span></span>  
 <span data-ttu-id="a8097-110">資料型別：服務</span><span class="sxs-lookup"><span data-stu-id="a8097-110">Data type: Service</span></span>  
<span data-ttu-id="a8097-111">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="a8097-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="a8097-112">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a8097-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8097-113">這個應用程式定義域的服務。</span><span class="sxs-lookup"><span data-stu-id="a8097-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a8097-114">ref</span><span class="sxs-lookup"><span data-stu-id="a8097-114">ref</span></span>  
 <span data-ttu-id="a8097-115">資料型別：AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="a8097-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="a8097-116">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="a8097-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="a8097-117">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a8097-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8097-118">包含應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8097-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8097-119">需求</span><span class="sxs-lookup"><span data-stu-id="a8097-119">Requirements</span></span>  
  
|<span data-ttu-id="a8097-120">MOF</span><span class="sxs-lookup"><span data-stu-id="a8097-120">MOF</span></span>|<span data-ttu-id="a8097-121">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a8097-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a8097-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="a8097-122">Namespace</span></span>|<span data-ttu-id="a8097-123">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a8097-123">Defined in root\ServiceModel</span></span>|
