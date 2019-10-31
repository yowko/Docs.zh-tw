---
title: EClrUnhandledException 列舉
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 302db0d029b3811d151473323a7a60bd16a00ec1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131241"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="9e5d2-102">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="9e5d2-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="9e5d2-103">描述可用來管理使用者程式碼中未處理之例外狀況的選項。</span><span class="sxs-lookup"><span data-stu-id="9e5d2-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e5d2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="9e5d2-105">Members</span><span class="sxs-lookup"><span data-stu-id="9e5d2-105">Members</span></span>  
  
|<span data-ttu-id="9e5d2-106">成員</span><span class="sxs-lookup"><span data-stu-id="9e5d2-106">Member</span></span>|<span data-ttu-id="9e5d2-107">描述</span><span class="sxs-lookup"><span data-stu-id="9e5d2-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="9e5d2-108">指定發生預設行為。</span><span class="sxs-lookup"><span data-stu-id="9e5d2-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="9e5d2-109">進程已損毀。</span><span class="sxs-lookup"><span data-stu-id="9e5d2-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="9e5d2-110">指定 common language runtime （CLR）會忽略未處理的例外狀況，並讓主機判斷任何進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="9e5d2-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e5d2-111">備註</span><span class="sxs-lookup"><span data-stu-id="9e5d2-111">Remarks</span></span>  
 <span data-ttu-id="9e5d2-112">若要指定 CLR 的行為與舊版相同，請使用 `eHostDeterminedPolicy` 成員。</span><span class="sxs-lookup"><span data-stu-id="9e5d2-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e5d2-113">需求</span><span class="sxs-lookup"><span data-stu-id="9e5d2-113">Requirements</span></span>  
 <span data-ttu-id="9e5d2-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e5d2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e5d2-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9e5d2-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e5d2-116">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="9e5d2-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e5d2-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e5d2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5d2-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e5d2-118">See also</span></span>

- [<span data-ttu-id="9e5d2-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="9e5d2-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="9e5d2-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="9e5d2-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="9e5d2-121">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9e5d2-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="9e5d2-122">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="9e5d2-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="9e5d2-123">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9e5d2-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="9e5d2-124">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="9e5d2-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
