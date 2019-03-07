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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49d7fb1de0b2ea63c1a766023b23acc42e027af8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475654"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="d93ca-102">ICorDebugILFrame::EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="d93ca-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="d93ca-103">取得列舉值的引數，這個框架中。</span><span class="sxs-lookup"><span data-stu-id="d93ca-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d93ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="d93ca-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d93ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="d93ca-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="d93ca-106">[out]ICorDebugValueEnum 物件，在此框架的引數的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d93ca-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d93ca-107">備註</span><span class="sxs-lookup"><span data-stu-id="d93ca-107">Remarks</span></span>  
 <span data-ttu-id="d93ca-108">`EnumerateArguments` 取得可以列出此 ICorDebugILFrame 物件所代表的呼叫框架中可用的引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d93ca-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="d93ca-109">此清單將包含所引數[vararg](/cpp/windows/vararg) （也就是可變數目的引數） 以及非引數`vararg`。</span><span class="sxs-lookup"><span data-stu-id="d93ca-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d93ca-110">需求</span><span class="sxs-lookup"><span data-stu-id="d93ca-110">Requirements</span></span>  
 <span data-ttu-id="d93ca-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d93ca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d93ca-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d93ca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d93ca-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d93ca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d93ca-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d93ca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
