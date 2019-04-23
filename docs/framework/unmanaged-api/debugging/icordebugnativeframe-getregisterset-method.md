---
title: ICorDebugNativeFrame::GetRegisterSet 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a4f7ecc227679e6b0afa29b20de1aefeae3b76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077916"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="cadd5-102">ICorDebugNativeFrame::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="cadd5-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="cadd5-103">取得這個堆疊框架設定暫存器。</span><span class="sxs-lookup"><span data-stu-id="cadd5-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadd5-104">語法</span><span class="sxs-lookup"><span data-stu-id="cadd5-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cadd5-105">參數</span><span class="sxs-lookup"><span data-stu-id="cadd5-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="cadd5-106">[out]位址指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)物件，代表註冊為此堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="cadd5-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cadd5-107">需求</span><span class="sxs-lookup"><span data-stu-id="cadd5-107">Requirements</span></span>  
 <span data-ttu-id="cadd5-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cadd5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadd5-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cadd5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cadd5-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cadd5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cadd5-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadd5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadd5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cadd5-112">See also</span></span>
