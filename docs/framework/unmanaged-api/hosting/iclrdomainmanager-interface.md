---
title: ICLRDomainManager 介面
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615705"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="dc1f7-102">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="dc1f7-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="dc1f7-103">可讓主機指定將用來初始化預設應用程式域的應用程式網域管理員，以及指定初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="dc1f7-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc1f7-104">方法</span><span class="sxs-lookup"><span data-stu-id="dc1f7-104">Methods</span></span>  
  
|<span data-ttu-id="dc1f7-105">方法</span><span class="sxs-lookup"><span data-stu-id="dc1f7-105">Method</span></span>|<span data-ttu-id="dc1f7-106">描述</span><span class="sxs-lookup"><span data-stu-id="dc1f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc1f7-107">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="dc1f7-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="dc1f7-108">指定 <xref:System.AppDomainManager?displayProperty=nameWithType> 將用來初始化預設應用程式域之應用程式網域管理員的類型（衍生自類別）。</span><span class="sxs-lookup"><span data-stu-id="dc1f7-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="dc1f7-109">SetPropertiesForDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="dc1f7-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="dc1f7-110">設定將用來初始化預設應用程式域的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc1f7-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc1f7-111">備註</span><span class="sxs-lookup"><span data-stu-id="dc1f7-111">Remarks</span></span>  
 <span data-ttu-id="dc1f7-112">若要取得此介面的實例，請使用 manager 類型 IID 呼叫[ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md)方法 `IID_ICLRDomainManager` 。</span><span class="sxs-lookup"><span data-stu-id="dc1f7-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1f7-113">需求</span><span class="sxs-lookup"><span data-stu-id="dc1f7-113">Requirements</span></span>  
 <span data-ttu-id="dc1f7-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc1f7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1f7-115">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="dc1f7-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dc1f7-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dc1f7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc1f7-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1f7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1f7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc1f7-118">See also</span></span>

- [<span data-ttu-id="dc1f7-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="dc1f7-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="dc1f7-120">裝載</span><span class="sxs-lookup"><span data-stu-id="dc1f7-120">Hosting</span></span>](index.md)
