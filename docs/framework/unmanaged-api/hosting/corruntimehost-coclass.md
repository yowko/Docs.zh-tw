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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616513"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="c8bf0-102">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="c8bf0-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="c8bf0-103">提供介面，以管理由 common language runtime 執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8bf0-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8bf0-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c8bf0-105">介面</span><span class="sxs-lookup"><span data-stu-id="c8bf0-105">Interfaces</span></span>  
  
|<span data-ttu-id="c8bf0-106">介面</span><span class="sxs-lookup"><span data-stu-id="c8bf0-106">Interface</span></span>|<span data-ttu-id="c8bf0-107">描述</span><span class="sxs-lookup"><span data-stu-id="c8bf0-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c8bf0-108">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="c8bf0-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="c8bf0-109">提供設定 common language runtime （CLR）的方法。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="c8bf0-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="c8bf0-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="c8bf0-111">提供的方法可讓主機明確啟動和停止 common language runtime、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="c8bf0-112">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c8bf0-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="c8bf0-113">提供方法來取得有關偵錯工具狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="c8bf0-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="c8bf0-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="c8bf0-115">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="c8bf0-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="c8bf0-116">"IValidator"</span></span>|<span data-ttu-id="c8bf0-117">提供可移植可執行映射的驗證方法，以及驗證錯誤的詳細報告。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8bf0-118">需求</span><span class="sxs-lookup"><span data-stu-id="c8bf0-118">Requirements</span></span>  
 <span data-ttu-id="c8bf0-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8bf0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8bf0-120">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="c8bf0-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c8bf0-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c8bf0-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8bf0-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8bf0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8bf0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8bf0-123">See also</span></span>

- [<span data-ttu-id="c8bf0-124">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="c8bf0-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
