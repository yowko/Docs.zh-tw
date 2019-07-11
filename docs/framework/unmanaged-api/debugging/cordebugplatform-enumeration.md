---
title: CorDebugPlatform 列舉
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c0644dc247225c510e1c84254417551b490416
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739674"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="5d199-102">CorDebugPlatform 列舉</span><span class="sxs-lookup"><span data-stu-id="5d199-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="5d199-103">提供所使用的目標平台值[icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5d199-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d199-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d199-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="5d199-105">成員</span><span class="sxs-lookup"><span data-stu-id="5d199-105">Members</span></span>  
  
|<span data-ttu-id="5d199-106">成員</span><span class="sxs-lookup"><span data-stu-id="5d199-106">Member</span></span>|<span data-ttu-id="5d199-107">說明</span><span class="sxs-lookup"><span data-stu-id="5d199-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5d199-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="5d199-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="5d199-109">目標平台是在 Intel x86 硬體上執行的 Windows。</span><span class="sxs-lookup"><span data-stu-id="5d199-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="5d199-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="5d199-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="5d199-111">目標平台是在 AMD64 或 Intel EM64T 硬體上執行的 64 位元 Windows。</span><span class="sxs-lookup"><span data-stu-id="5d199-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="5d199-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="5d199-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="5d199-113">目標平台是在 Intel IA-64 硬體上執行的 32 位元 Windows。</span><span class="sxs-lookup"><span data-stu-id="5d199-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="5d199-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="5d199-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="5d199-115">目標平台是在 PowerPC 硬體上執行的 Macintosh 作業系統。</span><span class="sxs-lookup"><span data-stu-id="5d199-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="5d199-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="5d199-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="5d199-117">目標平台是在 Intel x86 硬體上執行的 Macintosh 作業系統。</span><span class="sxs-lookup"><span data-stu-id="5d199-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="5d199-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="5d199-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="5d199-119">目標平台是在 Windows ARM 硬體上執行的 Macintosh 作業系統。</span><span class="sxs-lookup"><span data-stu-id="5d199-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="5d199-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="5d199-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="5d199-121">目標平台是在 AMD64 硬體上執行的 Macintosh 作業系統。</span><span class="sxs-lookup"><span data-stu-id="5d199-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d199-122">需求</span><span class="sxs-lookup"><span data-stu-id="5d199-122">Requirements</span></span>  
 <span data-ttu-id="5d199-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d199-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d199-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d199-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d199-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d199-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d199-126">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d199-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="5d199-127">.NET Framework 4.5.2 及更新版本中有提供 `CORDB_PLATFORM_WINDOWS_ARM` 及 `CORDB_PLATFORM_MAC_AMD64` 成員。</span><span class="sxs-lookup"><span data-stu-id="5d199-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d199-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d199-128">See also</span></span>

- [<span data-ttu-id="5d199-129">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5d199-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
