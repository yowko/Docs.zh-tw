---
title: ICorDebugObjectEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: 8e188f304908a8029a57bb059046205c35346f3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724685"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="1488e-102">ICorDebugObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="1488e-102">ICorDebugObjectEnum::Next Method</span></span>

<span data-ttu-id="1488e-103">從目前位置開始，取得列舉中指定物件數目 (Rva) 的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="1488e-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1488e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1488e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1488e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1488e-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="1488e-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="1488e-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="1488e-107">擴展指標的陣列，每個指標都會指向 CORDB_ADDRESS 物件。</span><span class="sxs-lookup"><span data-stu-id="1488e-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1488e-108">擴展實際傳回的物件數目指標。</span><span class="sxs-lookup"><span data-stu-id="1488e-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="1488e-109">如果是1，則這個值可能是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="1488e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1488e-110">需求</span><span class="sxs-lookup"><span data-stu-id="1488e-110">Requirements</span></span>  

 <span data-ttu-id="1488e-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1488e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1488e-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1488e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1488e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1488e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1488e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1488e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1488e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1488e-115">See also</span></span>
