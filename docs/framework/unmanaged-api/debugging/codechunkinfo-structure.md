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
ms.openlocfilehash: 36afee8af3de046683c55215a677a529b0837c77
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274260"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="0cf8a-102">CodeChunkInfo 結構</span><span class="sxs-lookup"><span data-stu-id="0cf8a-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="0cf8a-103">代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="0cf8a-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cf8a-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="0cf8a-105">成員</span><span class="sxs-lookup"><span data-stu-id="0cf8a-105">Members</span></span>  
  
|<span data-ttu-id="0cf8a-106">成員</span><span class="sxs-lookup"><span data-stu-id="0cf8a-106">Member</span></span>|<span data-ttu-id="0cf8a-107">描述</span><span class="sxs-lookup"><span data-stu-id="0cf8a-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="0cf8a-108">`CORDB_ADDRESS`值，指定區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="0cf8a-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="0cf8a-109">區塊的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0cf8a-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cf8a-110">備註</span><span class="sxs-lookup"><span data-stu-id="0cf8a-110">Remarks</span></span>  
 <span data-ttu-id="0cf8a-111">程式碼的單一區塊是機器碼的區域，而機器碼是程式碼物件的一部分，例如函式。</span><span class="sxs-lookup"><span data-stu-id="0cf8a-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cf8a-112">需求</span><span class="sxs-lookup"><span data-stu-id="0cf8a-112">Requirements</span></span>  
 <span data-ttu-id="0cf8a-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cf8a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf8a-114">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="0cf8a-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="0cf8a-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cf8a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cf8a-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf8a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf8a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cf8a-117">See also</span></span>

- [<span data-ttu-id="0cf8a-118">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="0cf8a-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="0cf8a-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="0cf8a-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0cf8a-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="0cf8a-120">Debugging</span></span>](index.md)
