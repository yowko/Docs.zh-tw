---
title: "ICorDebugNativeFrame::GetRegisterSet 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7689632d41971d85417501e9a7f90712a07b34bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="b6bad-102">ICorDebugNativeFrame::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="b6bad-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="b6bad-103">取得設定此堆疊框架的暫存器。</span><span class="sxs-lookup"><span data-stu-id="b6bad-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6bad-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6bad-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6bad-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6bad-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="b6bad-106">[out]位址指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)物件，代表登錄設定，此堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="b6bad-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6bad-107">需求</span><span class="sxs-lookup"><span data-stu-id="b6bad-107">Requirements</span></span>  
 <span data-ttu-id="b6bad-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6bad-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6bad-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6bad-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6bad-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6bad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6bad-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6bad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bad-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6bad-112">See Also</span></span>  
 
