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
ms.openlocfilehash: 63b07dda2293d3e05bd3c8fcdc45f20a498ea54c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616303"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="0a387-102">EClrUnhandledException 列舉</span><span class="sxs-lookup"><span data-stu-id="0a387-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="0a387-103">描述可用來管理使用者程式碼中未處理之例外狀況的選項。</span><span class="sxs-lookup"><span data-stu-id="0a387-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a387-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a387-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="0a387-105">成員</span><span class="sxs-lookup"><span data-stu-id="0a387-105">Members</span></span>  
  
|<span data-ttu-id="0a387-106">成員</span><span class="sxs-lookup"><span data-stu-id="0a387-106">Member</span></span>|<span data-ttu-id="0a387-107">說明</span><span class="sxs-lookup"><span data-stu-id="0a387-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="0a387-108">指定發生預設行為。</span><span class="sxs-lookup"><span data-stu-id="0a387-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="0a387-109">進程已損毀。</span><span class="sxs-lookup"><span data-stu-id="0a387-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="0a387-110">指定 common language runtime （CLR）會忽略未處理的例外狀況，並讓主機判斷任何進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="0a387-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a387-111">備註</span><span class="sxs-lookup"><span data-stu-id="0a387-111">Remarks</span></span>  
 <span data-ttu-id="0a387-112">若要指定 CLR 的行為與舊版相同，請使用 `eHostDeterminedPolicy` 成員。</span><span class="sxs-lookup"><span data-stu-id="0a387-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a387-113">需求</span><span class="sxs-lookup"><span data-stu-id="0a387-113">Requirements</span></span>  
 <span data-ttu-id="0a387-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a387-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a387-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0a387-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a387-116">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="0a387-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a387-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a387-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a387-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a387-118">See also</span></span>

- [<span data-ttu-id="0a387-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="0a387-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="0a387-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="0a387-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="0a387-121">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0a387-121">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="0a387-122">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="0a387-122">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="0a387-123">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="0a387-123">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="0a387-124">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="0a387-124">Hosting Enumerations</span></span>](hosting-enumerations.md)
