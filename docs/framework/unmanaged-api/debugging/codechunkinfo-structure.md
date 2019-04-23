---
title: CodeChunkInfo 結構
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58c9d4c66af0bb9f4e66d17b18ac78ef8271bc31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072658"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="67d3f-102">CodeChunkInfo 結構</span><span class="sxs-lookup"><span data-stu-id="67d3f-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="67d3f-103">代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="67d3f-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67d3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="67d3f-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="67d3f-105">成員</span><span class="sxs-lookup"><span data-stu-id="67d3f-105">Members</span></span>  
  
|<span data-ttu-id="67d3f-106">成員</span><span class="sxs-lookup"><span data-stu-id="67d3f-106">Member</span></span>|<span data-ttu-id="67d3f-107">描述</span><span class="sxs-lookup"><span data-stu-id="67d3f-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="67d3f-108">A`CORDB_ADDRESS`值，指定區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="67d3f-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="67d3f-109">以位元組為單位的區塊大小。</span><span class="sxs-lookup"><span data-stu-id="67d3f-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67d3f-110">備註</span><span class="sxs-lookup"><span data-stu-id="67d3f-110">Remarks</span></span>  
 <span data-ttu-id="67d3f-111">單一的程式碼區塊是物件的屬於程式碼，例如函式的原生程式碼的區域。</span><span class="sxs-lookup"><span data-stu-id="67d3f-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67d3f-112">需求</span><span class="sxs-lookup"><span data-stu-id="67d3f-112">Requirements</span></span>  
 <span data-ttu-id="67d3f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67d3f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d3f-114">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="67d3f-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="67d3f-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67d3f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67d3f-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d3f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d3f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67d3f-117">See also</span></span>

- [<span data-ttu-id="67d3f-118">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="67d3f-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="67d3f-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="67d3f-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="67d3f-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="67d3f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
