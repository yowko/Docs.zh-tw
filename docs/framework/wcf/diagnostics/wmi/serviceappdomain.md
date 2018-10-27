---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192235"
---
# <a name="serviceappdomain"></a><span data-ttu-id="fef72-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="fef72-102">ServiceAppDomain</span></span>
<span data-ttu-id="fef72-103">將服務對應至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="fef72-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef72-104">語法</span><span class="sxs-lookup"><span data-stu-id="fef72-104">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fef72-105">方法</span><span class="sxs-lookup"><span data-stu-id="fef72-105">Methods</span></span>  
 <span data-ttu-id="fef72-106">ServiceAppDomain 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="fef72-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fef72-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fef72-107">Properties</span></span>  
 <span data-ttu-id="fef72-108">ServiceAppDomain 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fef72-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="fef72-109">ref</span><span class="sxs-lookup"><span data-stu-id="fef72-109">ref</span></span>  
 <span data-ttu-id="fef72-110">資料型別：服務</span><span class="sxs-lookup"><span data-stu-id="fef72-110">Data type: Service</span></span>  
<span data-ttu-id="fef72-111">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="fef72-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="fef72-112">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fef72-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fef72-113">這個應用程式定義域的服務。</span><span class="sxs-lookup"><span data-stu-id="fef72-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="fef72-114">ref</span><span class="sxs-lookup"><span data-stu-id="fef72-114">ref</span></span>  
 <span data-ttu-id="fef72-115">資料型別：AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="fef72-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="fef72-116">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="fef72-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="fef72-117">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fef72-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fef72-118">包含應用程式定義域的屬性。</span><span class="sxs-lookup"><span data-stu-id="fef72-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef72-119">需求</span><span class="sxs-lookup"><span data-stu-id="fef72-119">Requirements</span></span>  
  
|<span data-ttu-id="fef72-120">MOF</span><span class="sxs-lookup"><span data-stu-id="fef72-120">MOF</span></span>|<span data-ttu-id="fef72-121">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="fef72-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fef72-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="fef72-122">Namespace</span></span>|<span data-ttu-id="fef72-123">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="fef72-123">Defined in root\ServiceModel</span></span>|
