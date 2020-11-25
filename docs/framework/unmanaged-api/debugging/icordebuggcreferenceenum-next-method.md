---
title: ICorDebugGCReferenceEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: e55c53b9610dcadee92ba9871bf52e3dacb5796b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726232"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="87cd6-102">ICorDebugGCReferenceEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="87cd6-102">ICorDebugGCReferenceEnum::Next Method</span></span>

<span data-ttu-id="87cd6-103">取得指定數目的 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 實例，其中包含將會進行垃圾收集之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="87cd6-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87cd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="87cd6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87cd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="87cd6-105">Parameters</span></span>  

 <span data-ttu-id="87cd6-106">celt</span><span class="sxs-lookup"><span data-stu-id="87cd6-106">celt</span></span>  
 <span data-ttu-id="87cd6-107">在要抓取的根目錄數目。</span><span class="sxs-lookup"><span data-stu-id="87cd6-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="87cd6-108">根</span><span class="sxs-lookup"><span data-stu-id="87cd6-108">roots</span></span>  
 <span data-ttu-id="87cd6-109">擴展指標的陣列，每個指標都會指向 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 物件，代表要進行垃圾收集之物件的根。</span><span class="sxs-lookup"><span data-stu-id="87cd6-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="87cd6-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="87cd6-110">pceltFetched</span></span>  
 <span data-ttu-id="87cd6-111">擴展實際傳回的 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 物件數目的指標 `roots` 。</span><span class="sxs-lookup"><span data-stu-id="87cd6-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="87cd6-112">如果 `celt` 為 1，則這個值可能是 `null`。</span><span class="sxs-lookup"><span data-stu-id="87cd6-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87cd6-113">備註</span><span class="sxs-lookup"><span data-stu-id="87cd6-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87cd6-114">需求</span><span class="sxs-lookup"><span data-stu-id="87cd6-114">Requirements</span></span>  

 <span data-ttu-id="87cd6-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87cd6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87cd6-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87cd6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87cd6-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87cd6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87cd6-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87cd6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cd6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87cd6-119">See also</span></span>

- [<span data-ttu-id="87cd6-120">ICorDebugGCReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="87cd6-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="87cd6-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="87cd6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
