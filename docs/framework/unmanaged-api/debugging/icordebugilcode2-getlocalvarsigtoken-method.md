---
title: "ICorDebugILCode2::GetLocalVarSigToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode2.GetLocalVarSigToken
api_location: mscordbi.dll
api_type: COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47004375194438b1ef0aaf61144ba6f16278545b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="8bd2f-102">ICorDebugILCode2::GetLocalVarSigToken 方法</span><span class="sxs-lookup"><span data-stu-id="8bd2f-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="8bd2f-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="8bd2f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8bd2f-104">針對此執行個體表示的函式，取得區域變數簽章的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8bd2f-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd2f-105">語法</span><span class="sxs-lookup"><span data-stu-id="8bd2f-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bd2f-106">參數</span><span class="sxs-lookup"><span data-stu-id="8bd2f-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="8bd2f-107">[out] 針對此函式的區域變數簽章，指向 `mdSignature` 語彙基元的指標，如果沒有簽章 (意即，如果函式沒有任何區域變數)，則指向 `mdSignatureNil`。</span><span class="sxs-lookup"><span data-stu-id="8bd2f-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd2f-108">備註</span><span class="sxs-lookup"><span data-stu-id="8bd2f-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd2f-109">需求</span><span class="sxs-lookup"><span data-stu-id="8bd2f-109">Requirements</span></span>  
 <span data-ttu-id="8bd2f-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8bd2f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd2f-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bd2f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bd2f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bd2f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bd2f-113">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd2f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd2f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8bd2f-114">See Also</span></span>  
 [<span data-ttu-id="8bd2f-115">ICorDebugILCode2 介面</span><span class="sxs-lookup"><span data-stu-id="8bd2f-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="8bd2f-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8bd2f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
