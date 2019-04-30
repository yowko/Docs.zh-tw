---
title: ICorDebugILFrame::EnumerateLocalVariables 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc9601105d05740e6db0a41bae521bd9a276d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988646"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="fdecc-102">ICorDebugILFrame::EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="fdecc-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="fdecc-103">取得這個框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fdecc-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdecc-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdecc-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdecc-105">參數</span><span class="sxs-lookup"><span data-stu-id="fdecc-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="fdecc-106">[out]ICorDebugValueEnum 物件，這個框架中區域變數的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="fdecc-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdecc-107">備註</span><span class="sxs-lookup"><span data-stu-id="fdecc-107">Remarks</span></span>  
 <span data-ttu-id="fdecc-108">`EnumerateLocalVariables` 取得可以列出可用此 ICorDebugILFrame 物件所代表的呼叫框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fdecc-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="fdecc-109">清單可能不包含所有的本機變數中執行的函式，因為其中部分可能不是作用中。</span><span class="sxs-lookup"><span data-stu-id="fdecc-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdecc-110">需求</span><span class="sxs-lookup"><span data-stu-id="fdecc-110">Requirements</span></span>  
 <span data-ttu-id="fdecc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdecc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdecc-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdecc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdecc-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdecc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdecc-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdecc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
