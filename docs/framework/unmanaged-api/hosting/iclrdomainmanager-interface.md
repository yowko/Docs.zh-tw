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
ms.openlocfilehash: a5abb601fe795a0c615403eec69f68ad9f66f00f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681167"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="1d6ae-102">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="1d6ae-102">ICLRDomainManager Interface</span></span>

<span data-ttu-id="1d6ae-103">讓主機指定將用來初始化預設應用程式域的應用程式域管理員，以及指定初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="1d6ae-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d6ae-104">方法</span><span class="sxs-lookup"><span data-stu-id="1d6ae-104">Methods</span></span>  
  
|<span data-ttu-id="1d6ae-105">方法</span><span class="sxs-lookup"><span data-stu-id="1d6ae-105">Method</span></span>|<span data-ttu-id="1d6ae-106">描述</span><span class="sxs-lookup"><span data-stu-id="1d6ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d6ae-107">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="1d6ae-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="1d6ae-108">指定 <xref:System.AppDomainManager?displayProperty=nameWithType> 將用來初始化預設應用程式域的應用程式域管理員型別，衍生自類別。</span><span class="sxs-lookup"><span data-stu-id="1d6ae-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="1d6ae-109">SetPropertiesForDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1d6ae-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="1d6ae-110">設定將用來初始化預設應用程式域的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d6ae-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d6ae-111">備註</span><span class="sxs-lookup"><span data-stu-id="1d6ae-111">Remarks</span></span>  

 <span data-ttu-id="1d6ae-112">若要取得這個介面的實例，請使用管理員類型 IID 來呼叫 [ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md) 方法 `IID_ICLRDomainManager` 。</span><span class="sxs-lookup"><span data-stu-id="1d6ae-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d6ae-113">需求</span><span class="sxs-lookup"><span data-stu-id="1d6ae-113">Requirements</span></span>  

 <span data-ttu-id="1d6ae-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d6ae-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d6ae-115">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="1d6ae-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1d6ae-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1d6ae-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d6ae-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d6ae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d6ae-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d6ae-118">See also</span></span>

- [<span data-ttu-id="1d6ae-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1d6ae-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1d6ae-120">裝載</span><span class="sxs-lookup"><span data-stu-id="1d6ae-120">Hosting</span></span>](index.md)
