---
title: CorRuntimeHost Coclass
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136899"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="079de-102">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="079de-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="079de-103">提供介面，以管理由 common language runtime 執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="079de-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079de-104">語法</span><span class="sxs-lookup"><span data-stu-id="079de-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="079de-105">介面</span><span class="sxs-lookup"><span data-stu-id="079de-105">Interfaces</span></span>  
  
|<span data-ttu-id="079de-106">介面</span><span class="sxs-lookup"><span data-stu-id="079de-106">Interface</span></span>|<span data-ttu-id="079de-107">描述</span><span class="sxs-lookup"><span data-stu-id="079de-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="079de-108">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="079de-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="079de-109">提供設定 common language runtime （CLR）的方法。</span><span class="sxs-lookup"><span data-stu-id="079de-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="079de-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="079de-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="079de-111">提供的方法可讓主機明確啟動和停止 common language runtime、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="079de-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="079de-112">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="079de-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="079de-113">提供方法來取得有關偵錯工具狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="079de-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="079de-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="079de-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="079de-115">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="079de-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="079de-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="079de-116">"IValidator"</span></span>|<span data-ttu-id="079de-117">提供可移植可執行映射的驗證方法，以及驗證錯誤的詳細報告。</span><span class="sxs-lookup"><span data-stu-id="079de-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="079de-118">需求</span><span class="sxs-lookup"><span data-stu-id="079de-118">Requirements</span></span>  
 <span data-ttu-id="079de-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="079de-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="079de-120">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="079de-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="079de-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="079de-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="079de-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="079de-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079de-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="079de-123">See also</span></span>

- [<span data-ttu-id="079de-124">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="079de-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
