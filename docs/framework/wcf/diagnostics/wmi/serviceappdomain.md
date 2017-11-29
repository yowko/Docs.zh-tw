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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="3f670-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="3f670-102">ServiceAppDomain</span></span>
<span data-ttu-id="3f670-103">將服務對應至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="3f670-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f670-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f670-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3f670-105">方法</span><span class="sxs-lookup"><span data-stu-id="3f670-105">Methods</span></span>  
 <span data-ttu-id="3f670-106">ServiceAppDomain 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="3f670-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3f670-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3f670-107">Properties</span></span>  
 <span data-ttu-id="3f670-108">ServiceAppDomain 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3f670-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3f670-109">ref</span><span class="sxs-lookup"><span data-stu-id="3f670-109">ref</span></span>  
 <span data-ttu-id="3f670-110">資料型別：服務</span><span class="sxs-lookup"><span data-stu-id="3f670-110">Data type: Service</span></span>  
<span data-ttu-id="3f670-111">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="3f670-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="3f670-112">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3f670-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f670-113">這個應用程式定義域的服務。</span><span class="sxs-lookup"><span data-stu-id="3f670-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3f670-114">ref</span><span class="sxs-lookup"><span data-stu-id="3f670-114">ref</span></span>  
 <span data-ttu-id="3f670-115">資料型別：AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="3f670-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="3f670-116">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="3f670-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="3f670-117">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3f670-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f670-118">包含應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f670-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f670-119">需求</span><span class="sxs-lookup"><span data-stu-id="3f670-119">Requirements</span></span>  
  
|<span data-ttu-id="3f670-120">MOF</span><span class="sxs-lookup"><span data-stu-id="3f670-120">MOF</span></span>|<span data-ttu-id="3f670-121">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="3f670-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3f670-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="3f670-122">Namespace</span></span>|<span data-ttu-id="3f670-123">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="3f670-123">Defined in root\ServiceModel</span></span>|
