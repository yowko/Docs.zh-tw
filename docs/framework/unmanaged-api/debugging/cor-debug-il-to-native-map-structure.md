---
title: "COR_DEBUG_IL_TO_NATIVE_MAP 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_DEBUG_IL_TO_NATIVE_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords: COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa191a4235defc5f47d0f7b3d823605da17fb5f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="2bbec-102">COR_DEBUG_IL_TO_NATIVE_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="2bbec-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="2bbec-103">包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。</span><span class="sxs-lookup"><span data-stu-id="2bbec-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbec-104">語法</span><span class="sxs-lookup"><span data-stu-id="2bbec-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="2bbec-105">成員</span><span class="sxs-lookup"><span data-stu-id="2bbec-105">Members</span></span>  
  
|<span data-ttu-id="2bbec-106">成員</span><span class="sxs-lookup"><span data-stu-id="2bbec-106">Member</span></span>|<span data-ttu-id="2bbec-107">說明</span><span class="sxs-lookup"><span data-stu-id="2bbec-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="2bbec-108">MSIL 程式碼的位移。</span><span class="sxs-lookup"><span data-stu-id="2bbec-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="2bbec-109">原生程式碼的開始位移。</span><span class="sxs-lookup"><span data-stu-id="2bbec-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="2bbec-110">原生程式碼結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="2bbec-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2bbec-111">需求</span><span class="sxs-lookup"><span data-stu-id="2bbec-111">Requirements</span></span>  
 <span data-ttu-id="2bbec-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2bbec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bbec-113">**標頭：** CorProf.idl、 CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="2bbec-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="2bbec-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bbec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bbec-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbec-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bbec-116">See Also</span></span>  
 [<span data-ttu-id="2bbec-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="2bbec-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [<span data-ttu-id="2bbec-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="2bbec-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="2bbec-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="2bbec-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="2bbec-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="2bbec-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
