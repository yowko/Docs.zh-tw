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
ms.openlocfilehash: b9b9b8a728932caa085bba1665dc97faf02be8fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431376"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="16233-102">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="16233-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="16233-103">提供介面來管理 common language runtime 所執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="16233-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16233-104">語法</span><span class="sxs-lookup"><span data-stu-id="16233-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="16233-105">介面</span><span class="sxs-lookup"><span data-stu-id="16233-105">Interfaces</span></span>  
  
|<span data-ttu-id="16233-106">介面</span><span class="sxs-lookup"><span data-stu-id="16233-106">Interface</span></span>|<span data-ttu-id="16233-107">描述</span><span class="sxs-lookup"><span data-stu-id="16233-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="16233-108">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="16233-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="16233-109">提供方法來設定 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="16233-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="16233-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="16233-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="16233-111">提供方法，讓主應用程式啟動和停止 common language runtime 明確地建立和設定應用程式定義域，若要存取的預設網域，並列舉處理序中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="16233-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="16233-112">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="16233-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="16233-113">提供方法來取得有關偵錯服務的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="16233-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="16233-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="16233-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="16233-115">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="16233-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="16233-116">「 IValidator"</span><span class="sxs-lookup"><span data-stu-id="16233-116">"IValidator"</span></span>|<span data-ttu-id="16233-117">提供方法進行驗證的可攜式執行檔影像，並驗證錯誤的詳細報告。</span><span class="sxs-lookup"><span data-stu-id="16233-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16233-118">需求</span><span class="sxs-lookup"><span data-stu-id="16233-118">Requirements</span></span>  
 <span data-ttu-id="16233-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16233-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16233-120">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="16233-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="16233-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="16233-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16233-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16233-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16233-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16233-123">See Also</span></span>  
 [<span data-ttu-id="16233-124">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="16233-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
