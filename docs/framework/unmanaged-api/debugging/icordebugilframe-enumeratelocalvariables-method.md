---
title: "ICorDebugILFrame::EnumerateLocalVariables 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a1b53dbefefcea6003ec4a61c8169ed96bac701
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="fb0d5-102">ICorDebugILFrame::EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="fb0d5-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="fb0d5-103">取得在這個框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fb0d5-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb0d5-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb0d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="fb0d5-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="fb0d5-106">[out]ICorDebugValueEnum 物件是這個框架中區域變數的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="fb0d5-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb0d5-107">備註</span><span class="sxs-lookup"><span data-stu-id="fb0d5-107">Remarks</span></span>  
 <span data-ttu-id="fb0d5-108">`EnumerateLocalVariables`取得可以列出可用此 ICorDebugILFrame 物件所代表的呼叫框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fb0d5-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="fb0d5-109">清單可能不包含所有的本機變數中執行的函式，因為其中部分可能不在作用中。</span><span class="sxs-lookup"><span data-stu-id="fb0d5-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb0d5-110">需求</span><span class="sxs-lookup"><span data-stu-id="fb0d5-110">Requirements</span></span>  
 <span data-ttu-id="fb0d5-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb0d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0d5-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb0d5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb0d5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb0d5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb0d5-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb0d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
