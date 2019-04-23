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
ms.openlocfilehash: 7e5fb3ab1d2dedb220fd4a486409512414233021
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176666"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="0d9d4-102">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="0d9d4-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="0d9d4-103">描述可用的選項，來管理使用者程式碼中未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0d9d4-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d9d4-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="0d9d4-105">成員</span><span class="sxs-lookup"><span data-stu-id="0d9d4-105">Members</span></span>  
  
|<span data-ttu-id="0d9d4-106">成員</span><span class="sxs-lookup"><span data-stu-id="0d9d4-106">Member</span></span>|<span data-ttu-id="0d9d4-107">描述</span><span class="sxs-lookup"><span data-stu-id="0d9d4-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="0d9d4-108">指定預設的行為就會發生。</span><span class="sxs-lookup"><span data-stu-id="0d9d4-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="0d9d4-109">此程序會終止。</span><span class="sxs-lookup"><span data-stu-id="0d9d4-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="0d9d4-110">指定 common language runtime (CLR) 會忽略未處理例外狀況，並可讓主機判斷任何進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="0d9d4-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d9d4-111">備註</span><span class="sxs-lookup"><span data-stu-id="0d9d4-111">Remarks</span></span>  
 <span data-ttu-id="0d9d4-112">若要指定 CLR 表現較早版本，請使用`eHostDeterminedPolicy`成員。</span><span class="sxs-lookup"><span data-stu-id="0d9d4-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d9d4-113">需求</span><span class="sxs-lookup"><span data-stu-id="0d9d4-113">Requirements</span></span>  
 <span data-ttu-id="0d9d4-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d9d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d9d4-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d9d4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d9d4-116">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d9d4-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d9d4-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d9d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9d4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9d4-118">See also</span></span>

- [<span data-ttu-id="0d9d4-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="0d9d4-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="0d9d4-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="0d9d4-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="0d9d4-121">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0d9d4-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="0d9d4-122">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="0d9d4-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="0d9d4-123">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0d9d4-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="0d9d4-124">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="0d9d4-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
