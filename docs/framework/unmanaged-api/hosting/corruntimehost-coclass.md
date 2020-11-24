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
ms.openlocfilehash: cd4e675b4ba50b47146428d204c28cc943c23c69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687999"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="187a2-102">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="187a2-102">CorRuntimeHost Coclass</span></span>

<span data-ttu-id="187a2-103">提供介面來管理 common language runtime 所執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="187a2-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="187a2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="187a2-104">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="187a2-105">介面</span><span class="sxs-lookup"><span data-stu-id="187a2-105">Interfaces</span></span>  
  
|<span data-ttu-id="187a2-106">介面</span><span class="sxs-lookup"><span data-stu-id="187a2-106">Interface</span></span>|<span data-ttu-id="187a2-107">描述</span><span class="sxs-lookup"><span data-stu-id="187a2-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="187a2-108">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="187a2-108">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="187a2-109">提供 (CLR) 設定 common language runtime 的方法。</span><span class="sxs-lookup"><span data-stu-id="187a2-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="187a2-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="187a2-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="187a2-111">提供的方法可讓主機明確地啟動及停止 common language runtime、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="187a2-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="187a2-112">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="187a2-112">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="187a2-113">提供方法，以取得有關偵錯工具狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="187a2-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="187a2-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="187a2-114">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="187a2-115">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="187a2-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="187a2-116">IValidator</span><span class="sxs-lookup"><span data-stu-id="187a2-116">"IValidator"</span></span>|<span data-ttu-id="187a2-117">提供驗證可攜式可執行檔映射和詳細報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="187a2-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="187a2-118">需求</span><span class="sxs-lookup"><span data-stu-id="187a2-118">Requirements</span></span>  

 <span data-ttu-id="187a2-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="187a2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="187a2-120">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="187a2-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="187a2-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="187a2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="187a2-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="187a2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187a2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="187a2-123">See also</span></span>

- [<span data-ttu-id="187a2-124">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="187a2-124">Hosting Coclasses</span></span>](hosting-coclasses.md)
