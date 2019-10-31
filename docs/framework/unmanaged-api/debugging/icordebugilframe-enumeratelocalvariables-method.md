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
ms.openlocfilehash: 07331a512dd513a94a7d8c3a8d8b0754d998b94b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131006"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="5bde5-102">ICorDebugILFrame::EnumerateLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="5bde5-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="5bde5-103">取得此框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5bde5-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bde5-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bde5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bde5-105">參數</span><span class="sxs-lookup"><span data-stu-id="5bde5-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="5bde5-106">脫銷ICorDebugValueEnum 物件位址的指標，這是此框架中區域變數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5bde5-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bde5-107">備註</span><span class="sxs-lookup"><span data-stu-id="5bde5-107">Remarks</span></span>  
 <span data-ttu-id="5bde5-108">`EnumerateLocalVariables` 取得列舉值，可列出這個 ICorDebugILFrame 物件所代表的呼叫框架中可用的區域變數。</span><span class="sxs-lookup"><span data-stu-id="5bde5-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="5bde5-109">清單可能不會包含執行中函式中的所有區域變數，因為其中有些變數可能不在作用中。</span><span class="sxs-lookup"><span data-stu-id="5bde5-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bde5-110">需求</span><span class="sxs-lookup"><span data-stu-id="5bde5-110">Requirements</span></span>  
 <span data-ttu-id="5bde5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bde5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bde5-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bde5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bde5-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bde5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bde5-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bde5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
