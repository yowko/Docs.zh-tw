---
title: ICorDebugILFrame::EnumerateArguments 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
ms.openlocfilehash: d74c5a6f966201c8ca9d2854de2e9986e7f1d0fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131033"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="d882f-102">ICorDebugILFrame::EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="d882f-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="d882f-103">取得此框架中引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d882f-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d882f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d882f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d882f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d882f-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="d882f-106">脫銷ICorDebugValueEnum 物件位址的指標，這是此框架中引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d882f-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d882f-107">備註</span><span class="sxs-lookup"><span data-stu-id="d882f-107">Remarks</span></span>  
 <span data-ttu-id="d882f-108">`EnumerateArguments` 取得列舉值，可列出此 ICorDebugILFrame 物件所代表的呼叫框架中可用的引數。</span><span class="sxs-lookup"><span data-stu-id="d882f-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="d882f-109">此清單會包含[vararg](/cpp/windows/vararg)的引數（也就是引數的可變數目）以及不 `vararg`的引數。</span><span class="sxs-lookup"><span data-stu-id="d882f-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d882f-110">需求</span><span class="sxs-lookup"><span data-stu-id="d882f-110">Requirements</span></span>  
 <span data-ttu-id="d882f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d882f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d882f-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d882f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d882f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d882f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d882f-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d882f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
