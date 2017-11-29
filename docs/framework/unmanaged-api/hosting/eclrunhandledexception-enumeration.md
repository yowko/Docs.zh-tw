---
title: "EClrUnhandledException 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67787072779e0cb22a339c2d13c972ba36f3ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="43cae-102">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="43cae-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="43cae-103">描述可用於管理使用者程式碼中未處理的例外狀況的選項。</span><span class="sxs-lookup"><span data-stu-id="43cae-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43cae-104">語法</span><span class="sxs-lookup"><span data-stu-id="43cae-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="43cae-105">成員</span><span class="sxs-lookup"><span data-stu-id="43cae-105">Members</span></span>  
  
|<span data-ttu-id="43cae-106">成員</span><span class="sxs-lookup"><span data-stu-id="43cae-106">Member</span></span>|<span data-ttu-id="43cae-107">說明</span><span class="sxs-lookup"><span data-stu-id="43cae-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="43cae-108">指定預設的行為就會發生。</span><span class="sxs-lookup"><span data-stu-id="43cae-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="43cae-109">處理程序會終止。</span><span class="sxs-lookup"><span data-stu-id="43cae-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="43cae-110">指定 common language runtime (CLR) 會忽略未處理例外狀況，並可讓主機判斷任何進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="43cae-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43cae-111">備註</span><span class="sxs-lookup"><span data-stu-id="43cae-111">Remarks</span></span>  
 <span data-ttu-id="43cae-112">若要指定 CLR 行為類似較早版本，請使用`eHostDeterminedPolicy`成員。</span><span class="sxs-lookup"><span data-stu-id="43cae-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43cae-113">需求</span><span class="sxs-lookup"><span data-stu-id="43cae-113">Requirements</span></span>  
 <span data-ttu-id="43cae-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43cae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43cae-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43cae-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43cae-116">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43cae-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43cae-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43cae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43cae-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43cae-118">See Also</span></span>  
 [<span data-ttu-id="43cae-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="43cae-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="43cae-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="43cae-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="43cae-121">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="43cae-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="43cae-122">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="43cae-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="43cae-123">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="43cae-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="43cae-124">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="43cae-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
