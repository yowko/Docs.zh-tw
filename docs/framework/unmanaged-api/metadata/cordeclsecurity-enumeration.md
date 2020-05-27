---
title: CorDeclSecurity 列舉
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: ffbc9a10ff48b3dfd59b95c0f6b9ecab80b6a49c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007880"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="da1a3-102">CorDeclSecurity 列舉</span><span class="sxs-lookup"><span data-stu-id="da1a3-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="da1a3-103">指定可以使用宣告式安全性執行的安全性動作。</span><span class="sxs-lookup"><span data-stu-id="da1a3-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="da1a3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="da1a3-105">成員</span><span class="sxs-lookup"><span data-stu-id="da1a3-105">Members</span></span>  
  
|<span data-ttu-id="da1a3-106">成員</span><span class="sxs-lookup"><span data-stu-id="da1a3-106">Member</span></span>|<span data-ttu-id="da1a3-107">描述</span><span class="sxs-lookup"><span data-stu-id="da1a3-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="da1a3-108">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="da1a3-109">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="da1a3-110">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="da1a3-111">呼叫堆疊中較高層的所有呼叫端，必須已獲得目前權限物件所指定的權限。</span><span class="sxs-lookup"><span data-stu-id="da1a3-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="da1a3-112">呼叫程式碼可以存取目前權限物件所識別的資源，即使堆疊中較高層的呼叫端未獲得存取資源的許可權也一樣。</span><span class="sxs-lookup"><span data-stu-id="da1a3-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="da1a3-113">存取目前權限物件所指定之資源的能力，會被拒絕呼叫端，即使已授與存取權。</span><span class="sxs-lookup"><span data-stu-id="da1a3-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="da1a3-114">只可存取這個權限物件所指定的資源，即使程式碼已獲得其他資源存取權限亦然。</span><span class="sxs-lookup"><span data-stu-id="da1a3-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="da1a3-115">立即呼叫端必須在指定的時間內被授與指定的許可權。</span><span class="sxs-lookup"><span data-stu-id="da1a3-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="da1a3-116">繼承另一個類別或覆寫方法的衍生類別，必須已授與指定的許可權。</span><span class="sxs-lookup"><span data-stu-id="da1a3-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="da1a3-117">呼叫端可以要求執行程式碼所需的最小許可權。</span><span class="sxs-lookup"><span data-stu-id="da1a3-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="da1a3-118">這個動作只能在組件的範圍內使用。</span><span class="sxs-lookup"><span data-stu-id="da1a3-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="da1a3-119">呼叫端可以要求選擇性的其他許可權（不需要執行）。</span><span class="sxs-lookup"><span data-stu-id="da1a3-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="da1a3-120">這項要求會隱含拒絕未特別要求的所有其他權限。</span><span class="sxs-lookup"><span data-stu-id="da1a3-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="da1a3-121">這個動作只能在組件的範圍內使用。</span><span class="sxs-lookup"><span data-stu-id="da1a3-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="da1a3-122">系統將不會授與呼叫者對可能誤用之許可權的要求。</span><span class="sxs-lookup"><span data-stu-id="da1a3-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="da1a3-123">這個動作只能在組件的範圍內使用。</span><span class="sxs-lookup"><span data-stu-id="da1a3-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="da1a3-124">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="da1a3-125">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="da1a3-126">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="da1a3-127">直接呼叫端必須已獲得指定權限。</span><span class="sxs-lookup"><span data-stu-id="da1a3-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="da1a3-128">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="da1a3-129">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="da1a3-130">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="da1a3-131">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="da1a3-132">已保留。</span><span class="sxs-lookup"><span data-stu-id="da1a3-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da1a3-133">需求</span><span class="sxs-lookup"><span data-stu-id="da1a3-133">Requirements</span></span>  
 <span data-ttu-id="da1a3-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da1a3-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da1a3-135">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="da1a3-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="da1a3-136">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da1a3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1a3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da1a3-137">See also</span></span>

- [<span data-ttu-id="da1a3-138">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="da1a3-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
