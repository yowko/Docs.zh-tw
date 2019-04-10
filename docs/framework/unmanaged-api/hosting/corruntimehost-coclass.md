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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2143fc13db1757ac2fa8a9c5a43f104a0c519ca0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218559"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="cb8d1-102">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="cb8d1-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="cb8d1-103">提供介面來管理由 common language runtime 所執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb8d1-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="cb8d1-105">介面</span><span class="sxs-lookup"><span data-stu-id="cb8d1-105">Interfaces</span></span>  
  
|<span data-ttu-id="cb8d1-106">介面</span><span class="sxs-lookup"><span data-stu-id="cb8d1-106">Interface</span></span>|<span data-ttu-id="cb8d1-107">描述</span><span class="sxs-lookup"><span data-stu-id="cb8d1-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="cb8d1-108">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="cb8d1-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="cb8d1-109">提供用於設定 common language runtime (CLR) 方法。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="cb8d1-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="cb8d1-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="cb8d1-111">提供方法，讓主應用程式啟動，並明確地停止通用語言執行平台，來建立及設定應用程式定義域，若要存取預設網域，並列舉處理序中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="cb8d1-112">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="cb8d1-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="cb8d1-113">提供方法來取得有關偵錯服務的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="cb8d1-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="cb8d1-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="cb8d1-115">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="cb8d1-116">「 IValidator"</span><span class="sxs-lookup"><span data-stu-id="cb8d1-116">"IValidator"</span></span>|<span data-ttu-id="cb8d1-117">提供用於驗證的可攜式執行檔映像和詳細報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb8d1-118">需求</span><span class="sxs-lookup"><span data-stu-id="cb8d1-118">Requirements</span></span>  
 <span data-ttu-id="cb8d1-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb8d1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8d1-120">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="cb8d1-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="cb8d1-121">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cb8d1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cb8d1-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="cb8d1-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb8d1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb8d1-123">See also</span></span>

- [<span data-ttu-id="cb8d1-124">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="cb8d1-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
