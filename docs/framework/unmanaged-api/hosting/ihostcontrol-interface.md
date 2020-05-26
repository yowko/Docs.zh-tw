---
title: IHostControl 介面
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804927"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="976fb-102">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="976fb-102">IHostControl Interface</span></span>
<span data-ttu-id="976fb-103">提供設定元件載入的方法，以及判斷主機支援的主控介面。</span><span class="sxs-lookup"><span data-stu-id="976fb-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="976fb-104">方法</span><span class="sxs-lookup"><span data-stu-id="976fb-104">Methods</span></span>  
  
|<span data-ttu-id="976fb-105">方法</span><span class="sxs-lookup"><span data-stu-id="976fb-105">Method</span></span>|<span data-ttu-id="976fb-106">描述</span><span class="sxs-lookup"><span data-stu-id="976fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="976fb-107">GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="976fb-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="976fb-108">取得具有指定之之介面的主機介面指標 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="976fb-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="976fb-109">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="976fb-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="976fb-110">通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="976fb-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="976fb-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="976fb-111">Requirements</span></span>  
 <span data-ttu-id="976fb-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="976fb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="976fb-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="976fb-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="976fb-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="976fb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="976fb-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="976fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="976fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="976fb-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="976fb-117">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="976fb-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="976fb-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="976fb-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="976fb-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="976fb-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
