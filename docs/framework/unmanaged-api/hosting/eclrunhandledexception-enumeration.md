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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba0c2ea7733f098b7fac95f51b5eb16d083174e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779374"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="09bef-102">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="09bef-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="09bef-103">描述可用的選項，來管理使用者程式碼中未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="09bef-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09bef-104">語法</span><span class="sxs-lookup"><span data-stu-id="09bef-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="09bef-105">成員</span><span class="sxs-lookup"><span data-stu-id="09bef-105">Members</span></span>  
  
|<span data-ttu-id="09bef-106">成員</span><span class="sxs-lookup"><span data-stu-id="09bef-106">Member</span></span>|<span data-ttu-id="09bef-107">描述</span><span class="sxs-lookup"><span data-stu-id="09bef-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="09bef-108">指定預設的行為就會發生。</span><span class="sxs-lookup"><span data-stu-id="09bef-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="09bef-109">此程序會終止。</span><span class="sxs-lookup"><span data-stu-id="09bef-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="09bef-110">指定 common language runtime (CLR) 會忽略未處理例外狀況，並可讓主機判斷任何進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="09bef-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09bef-111">備註</span><span class="sxs-lookup"><span data-stu-id="09bef-111">Remarks</span></span>  
 <span data-ttu-id="09bef-112">若要指定 CLR 表現較早版本，請使用`eHostDeterminedPolicy`成員。</span><span class="sxs-lookup"><span data-stu-id="09bef-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09bef-113">需求</span><span class="sxs-lookup"><span data-stu-id="09bef-113">Requirements</span></span>  
 <span data-ttu-id="09bef-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09bef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09bef-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09bef-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09bef-116">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09bef-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09bef-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09bef-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09bef-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09bef-118">See also</span></span>

- [<span data-ttu-id="09bef-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="09bef-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="09bef-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="09bef-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="09bef-121">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="09bef-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="09bef-122">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="09bef-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="09bef-123">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="09bef-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="09bef-124">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="09bef-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
