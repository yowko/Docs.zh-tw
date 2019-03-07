---
title: ICorDebugILFrame::GetLocalVariable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd36f01297f24c050f84fb67e7673f8641fe206
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475238"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="0fc8d-102">ICorDebugILFrame::GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="0fc8d-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="0fc8d-103">在此 Microsoft intermediate language (MSIL) 堆疊框架中取得指定的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fc8d-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fc8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0fc8d-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="0fc8d-106">[in]在此 MSIL 堆疊框架中區域變數的索引。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0fc8d-107">[out]ICorDebugValue 物件，表示擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fc8d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0fc8d-108">Remarks</span></span>  
 <span data-ttu-id="0fc8d-109">`GetLocalVariable`方法可以用在 MSIL 堆疊框架中或在 just-in-time (JIT) 編譯過的框架中。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fc8d-110">需求</span><span class="sxs-lookup"><span data-stu-id="0fc8d-110">Requirements</span></span>  
 <span data-ttu-id="0fc8d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fc8d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fc8d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fc8d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fc8d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fc8d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fc8d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
