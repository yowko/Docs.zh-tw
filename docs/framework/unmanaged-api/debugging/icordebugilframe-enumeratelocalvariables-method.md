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
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178834"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="a38f5-102">ICorDebugILFrame::EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="a38f5-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="a38f5-103">獲取此幀中區域變數的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="a38f5-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a38f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="a38f5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a38f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="a38f5-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="a38f5-106">[out] ICorDebugValueEnum 物件的位址指標，此物件是這個框架中區域變數的列舉程式。</span><span class="sxs-lookup"><span data-stu-id="a38f5-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a38f5-107">備註</span><span class="sxs-lookup"><span data-stu-id="a38f5-107">Remarks</span></span>  
 <span data-ttu-id="a38f5-108">`EnumerateLocalVariables`獲取一個枚舉器，該枚舉器可以列出此 ICorDebugILFrame 物件表示的調用幀中可用的區域變數。</span><span class="sxs-lookup"><span data-stu-id="a38f5-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="a38f5-109">該清單可能不包括正在運行的函數中的所有區域變數，因為其中一些變數可能未處於活動狀態。</span><span class="sxs-lookup"><span data-stu-id="a38f5-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a38f5-110">需求</span><span class="sxs-lookup"><span data-stu-id="a38f5-110">Requirements</span></span>  
 <span data-ttu-id="a38f5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a38f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a38f5-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a38f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a38f5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a38f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a38f5-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
