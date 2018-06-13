---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485664"
---
# <a name="serviceappdomain"></a><span data-ttu-id="b85e0-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="b85e0-102">ServiceAppDomain</span></span>
<span data-ttu-id="b85e0-103">將服務對應至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="b85e0-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b85e0-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b85e0-105">方法</span><span class="sxs-lookup"><span data-stu-id="b85e0-105">Methods</span></span>  
 <span data-ttu-id="b85e0-106">ServiceAppDomain 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="b85e0-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b85e0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b85e0-107">Properties</span></span>  
 <span data-ttu-id="b85e0-108">ServiceAppDomain 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b85e0-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b85e0-109">ref</span><span class="sxs-lookup"><span data-stu-id="b85e0-109">ref</span></span>  
 <span data-ttu-id="b85e0-110">資料型別：服務</span><span class="sxs-lookup"><span data-stu-id="b85e0-110">Data type: Service</span></span>  
<span data-ttu-id="b85e0-111">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="b85e0-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="b85e0-112">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="b85e0-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b85e0-113">這個應用程式定義域的服務。</span><span class="sxs-lookup"><span data-stu-id="b85e0-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b85e0-114">ref</span><span class="sxs-lookup"><span data-stu-id="b85e0-114">ref</span></span>  
 <span data-ttu-id="b85e0-115">資料型別：AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="b85e0-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="b85e0-116">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="b85e0-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="b85e0-117">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="b85e0-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b85e0-118">包含應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="b85e0-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b85e0-119">需求</span><span class="sxs-lookup"><span data-stu-id="b85e0-119">Requirements</span></span>  
  
|<span data-ttu-id="b85e0-120">MOF</span><span class="sxs-lookup"><span data-stu-id="b85e0-120">MOF</span></span>|<span data-ttu-id="b85e0-121">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="b85e0-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b85e0-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="b85e0-122">Namespace</span></span>|<span data-ttu-id="b85e0-123">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="b85e0-123">Defined in root\ServiceModel</span></span>|
