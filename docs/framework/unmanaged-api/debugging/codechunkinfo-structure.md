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
ms.openlocfilehash: 11197246662a93f6a8b57c6e61e49505a9999d00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727428"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="5467e-102">CodeChunkInfo 結構</span><span class="sxs-lookup"><span data-stu-id="5467e-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="5467e-103">代表記憶體中的單一程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="5467e-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5467e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5467e-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="5467e-105">成員</span><span class="sxs-lookup"><span data-stu-id="5467e-105">Members</span></span>  
  
|<span data-ttu-id="5467e-106">member</span><span class="sxs-lookup"><span data-stu-id="5467e-106">Member</span></span>|<span data-ttu-id="5467e-107">描述</span><span class="sxs-lookup"><span data-stu-id="5467e-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="5467e-108">`CORDB_ADDRESS`值，指定區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="5467e-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="5467e-109">區塊的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5467e-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5467e-110">備註</span><span class="sxs-lookup"><span data-stu-id="5467e-110">Remarks</span></span>  

 <span data-ttu-id="5467e-111">程式碼的單一區塊是機器碼的區域，其為程式碼物件的一部分，例如函數。</span><span class="sxs-lookup"><span data-stu-id="5467e-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5467e-112">需求</span><span class="sxs-lookup"><span data-stu-id="5467e-112">Requirements</span></span>  

 <span data-ttu-id="5467e-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5467e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5467e-114">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="5467e-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="5467e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5467e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5467e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5467e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5467e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5467e-117">See also</span></span>

- [<span data-ttu-id="5467e-118">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="5467e-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="5467e-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="5467e-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5467e-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="5467e-120">Debugging</span></span>](index.md)
