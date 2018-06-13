---
title: COR_DEBUG_IL_TO_NATIVE_MAP 結構
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ea9a75ae9316c18439f6c2b728b47deacef9228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404727"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="cceb5-102">COR_DEBUG_IL_TO_NATIVE_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="cceb5-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="cceb5-103">包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。</span><span class="sxs-lookup"><span data-stu-id="cceb5-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cceb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="cceb5-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="cceb5-105">成員</span><span class="sxs-lookup"><span data-stu-id="cceb5-105">Members</span></span>  
  
|<span data-ttu-id="cceb5-106">成員</span><span class="sxs-lookup"><span data-stu-id="cceb5-106">Member</span></span>|<span data-ttu-id="cceb5-107">描述</span><span class="sxs-lookup"><span data-stu-id="cceb5-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="cceb5-108">MSIL 程式碼的位移。</span><span class="sxs-lookup"><span data-stu-id="cceb5-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="cceb5-109">原生程式碼的開始位移。</span><span class="sxs-lookup"><span data-stu-id="cceb5-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="cceb5-110">原生程式碼結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="cceb5-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cceb5-111">需求</span><span class="sxs-lookup"><span data-stu-id="cceb5-111">Requirements</span></span>  
 <span data-ttu-id="cceb5-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cceb5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cceb5-113">**標頭：** CorProf.idl、 CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="cceb5-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="cceb5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cceb5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cceb5-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cceb5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cceb5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cceb5-116">See Also</span></span>  
 [<span data-ttu-id="cceb5-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="cceb5-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [<span data-ttu-id="cceb5-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="cceb5-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="cceb5-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="cceb5-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="cceb5-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="cceb5-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
