---
title: ICorDebugProcess5::EnumerateGCReferences 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 0f2f5acfc6a23398b15af3a63345050eb0dfd5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687186"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="a27e4-102">ICorDebugProcess5::EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="a27e4-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>

<span data-ttu-id="a27e4-103">取得要在進程中進行垃圾收集之所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a27e4-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="a27e4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a27e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="a27e4-105">Parameters</span></span>  

 `enumerateWeakReferences`  
 <span data-ttu-id="a27e4-106">在布林值，指出是否也要列舉弱式參考。</span><span class="sxs-lookup"><span data-stu-id="a27e4-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="a27e4-107">如果 `enumerateWeakReferences` 為 `true` ，則 `ppEnum` 列舉值包含強式參考和弱式參考。</span><span class="sxs-lookup"><span data-stu-id="a27e4-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="a27e4-108">如果 `enumerateWeakReferences` 為 `false` ，則列舉值只會包含強式參考。</span><span class="sxs-lookup"><span data-stu-id="a27e4-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="a27e4-109">擴展 [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) 位址的指標，其為要進行垃圾收集之物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a27e4-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a27e4-110">備註</span><span class="sxs-lookup"><span data-stu-id="a27e4-110">Remarks</span></span>  

 <span data-ttu-id="a27e4-111">這個方法會提供一種方法來判斷進程中任何 managed 物件的完整根鏈，而且可以用來判斷物件仍在運作中的原因。</span><span class="sxs-lookup"><span data-stu-id="a27e4-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a27e4-112">需求</span><span class="sxs-lookup"><span data-stu-id="a27e4-112">Requirements</span></span>  

 <span data-ttu-id="a27e4-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a27e4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a27e4-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a27e4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a27e4-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a27e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a27e4-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a27e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27e4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a27e4-117">See also</span></span>

- [<span data-ttu-id="a27e4-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="a27e4-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a27e4-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a27e4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
