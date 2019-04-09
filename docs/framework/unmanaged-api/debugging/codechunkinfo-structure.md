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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072658"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="8dd42-102">CodeChunkInfo 結構</span><span class="sxs-lookup"><span data-stu-id="8dd42-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="8dd42-103">代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="8dd42-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd42-104">語法</span><span class="sxs-lookup"><span data-stu-id="8dd42-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="8dd42-105">成員</span><span class="sxs-lookup"><span data-stu-id="8dd42-105">Members</span></span>  
  
|<span data-ttu-id="8dd42-106">成員</span><span class="sxs-lookup"><span data-stu-id="8dd42-106">Member</span></span>|<span data-ttu-id="8dd42-107">描述</span><span class="sxs-lookup"><span data-stu-id="8dd42-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="8dd42-108">A`CORDB_ADDRESS`值，指定區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="8dd42-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="8dd42-109">以位元組為單位的區塊大小。</span><span class="sxs-lookup"><span data-stu-id="8dd42-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dd42-110">備註</span><span class="sxs-lookup"><span data-stu-id="8dd42-110">Remarks</span></span>  
 <span data-ttu-id="8dd42-111">單一的程式碼區塊是物件的屬於程式碼，例如函式的原生程式碼的區域。</span><span class="sxs-lookup"><span data-stu-id="8dd42-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dd42-112">需求</span><span class="sxs-lookup"><span data-stu-id="8dd42-112">Requirements</span></span>  
 <span data-ttu-id="8dd42-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd42-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dd42-114">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8dd42-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8dd42-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8dd42-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8dd42-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8dd42-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8dd42-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd42-117">See also</span></span>

- [<span data-ttu-id="8dd42-118">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="8dd42-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="8dd42-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="8dd42-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="8dd42-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="8dd42-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
