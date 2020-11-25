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
ms.openlocfilehash: 968ceec53aade3d04c500c8247d397ffb71382c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703183"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="bb918-102">ICorDebugILFrame::EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="bb918-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>

<span data-ttu-id="bb918-103">取得這個框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bb918-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb918-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb918-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb918-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb918-105">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="bb918-106">[out] ICorDebugValueEnum 物件的位址指標，此物件是這個框架中區域變數的列舉程式。</span><span class="sxs-lookup"><span data-stu-id="bb918-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb918-107">備註</span><span class="sxs-lookup"><span data-stu-id="bb918-107">Remarks</span></span>  

 <span data-ttu-id="bb918-108">`EnumerateLocalVariables` 取得列舉值，這個列舉值可以列出這個 ICorDebugILFrame 物件所表示之呼叫框架中可用的區域變數。</span><span class="sxs-lookup"><span data-stu-id="bb918-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="bb918-109">此清單可能不會包含執行的函式中的所有區域變數，因為其中有些變數可能不在作用中。</span><span class="sxs-lookup"><span data-stu-id="bb918-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb918-110">需求</span><span class="sxs-lookup"><span data-stu-id="bb918-110">Requirements</span></span>  

 <span data-ttu-id="bb918-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb918-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb918-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb918-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb918-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb918-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb918-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb918-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
