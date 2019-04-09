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
ms.openlocfilehash: 03ce77dd7407db8289abfefba13d71a9af053e10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142047"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="49a48-102">COR_DEBUG_IL_TO_NATIVE_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="49a48-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="49a48-103">包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。</span><span class="sxs-lookup"><span data-stu-id="49a48-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a48-104">語法</span><span class="sxs-lookup"><span data-stu-id="49a48-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="49a48-105">成員</span><span class="sxs-lookup"><span data-stu-id="49a48-105">Members</span></span>  
  
|<span data-ttu-id="49a48-106">成員</span><span class="sxs-lookup"><span data-stu-id="49a48-106">Member</span></span>|<span data-ttu-id="49a48-107">描述</span><span class="sxs-lookup"><span data-stu-id="49a48-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="49a48-108">MSIL 程式碼的位移。</span><span class="sxs-lookup"><span data-stu-id="49a48-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="49a48-109">原生程式碼開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="49a48-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="49a48-110">原生程式碼結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="49a48-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49a48-111">需求</span><span class="sxs-lookup"><span data-stu-id="49a48-111">Requirements</span></span>  
 <span data-ttu-id="49a48-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49a48-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49a48-113">**標頭：** CorProf.idl CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="49a48-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="49a48-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49a48-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="49a48-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="49a48-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="49a48-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49a48-116">See also</span></span>

- [<span data-ttu-id="49a48-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="49a48-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="49a48-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="49a48-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="49a48-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="49a48-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="49a48-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="49a48-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
