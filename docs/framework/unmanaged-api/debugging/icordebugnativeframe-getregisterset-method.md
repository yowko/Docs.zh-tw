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
ms.openlocfilehash: e2055098c85c5a2e4619b9b0ddc8d602256bd16b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209717"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="f73c2-102">ICorDebugNativeFrame::GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="f73c2-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="f73c2-103">取得這個堆疊框架的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="f73c2-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f73c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="f73c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f73c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="f73c2-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="f73c2-106">脫銷[ICorDebugRegisterSet](icordebugregisterset-interface.md)物件位址的指標，代表此堆疊框架的緩存集。</span><span class="sxs-lookup"><span data-stu-id="f73c2-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f73c2-107">需求</span><span class="sxs-lookup"><span data-stu-id="f73c2-107">Requirements</span></span>  
 <span data-ttu-id="f73c2-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f73c2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f73c2-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f73c2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f73c2-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f73c2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f73c2-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f73c2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73c2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f73c2-112">See also</span></span>
