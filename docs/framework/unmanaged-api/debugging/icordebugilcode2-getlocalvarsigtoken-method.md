---
title: ICorDebugILCode2::GetLocalVarSigToken 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9810a8a55fc9c5296bffa5106551f9734dcd61bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199904"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="e0460-102">ICorDebugILCode2::GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="e0460-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="e0460-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="e0460-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e0460-104">針對此執行個體表示的函式，取得區域變數簽章的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e0460-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0460-105">語法</span><span class="sxs-lookup"><span data-stu-id="e0460-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0460-106">參數</span><span class="sxs-lookup"><span data-stu-id="e0460-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="e0460-107">[out] 針對此函式的區域變數簽章，指向 `mdSignature` 語彙基元的指標，如果沒有簽章 (意即，如果函式沒有任何區域變數)，則指向 `mdSignatureNil`。</span><span class="sxs-lookup"><span data-stu-id="e0460-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0460-108">備註</span><span class="sxs-lookup"><span data-stu-id="e0460-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0460-109">需求</span><span class="sxs-lookup"><span data-stu-id="e0460-109">Requirements</span></span>  
 <span data-ttu-id="e0460-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0460-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0460-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0460-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0460-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0460-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0460-113">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0460-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0460-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0460-114">See also</span></span>

- [<span data-ttu-id="e0460-115">ICorDebugILCode2 介面</span><span class="sxs-lookup"><span data-stu-id="e0460-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="e0460-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0460-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
