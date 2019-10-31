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
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132392"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="44380-102">CodeChunkInfo 結構</span><span class="sxs-lookup"><span data-stu-id="44380-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="44380-103">代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="44380-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44380-104">語法</span><span class="sxs-lookup"><span data-stu-id="44380-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="44380-105">Members</span><span class="sxs-lookup"><span data-stu-id="44380-105">Members</span></span>  
  
|<span data-ttu-id="44380-106">成員</span><span class="sxs-lookup"><span data-stu-id="44380-106">Member</span></span>|<span data-ttu-id="44380-107">描述</span><span class="sxs-lookup"><span data-stu-id="44380-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="44380-108">`CORDB_ADDRESS` 值，指定區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="44380-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="44380-109">區塊的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="44380-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44380-110">備註</span><span class="sxs-lookup"><span data-stu-id="44380-110">Remarks</span></span>  
 <span data-ttu-id="44380-111">程式碼的單一區塊是機器碼的區域，而機器碼是程式碼物件的一部分，例如函式。</span><span class="sxs-lookup"><span data-stu-id="44380-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44380-112">需求</span><span class="sxs-lookup"><span data-stu-id="44380-112">Requirements</span></span>  
 <span data-ttu-id="44380-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44380-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44380-114">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="44380-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="44380-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44380-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44380-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44380-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44380-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="44380-117">See also</span></span>

- [<span data-ttu-id="44380-118">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="44380-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="44380-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="44380-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="44380-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="44380-120">Debugging</span></span>](index.md)
