---
title: ICorDebugILFrame::GetArgument 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46852ed8ac53c3a7720edff4833f3dc3cce42bbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995523"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="5cf17-102">ICorDebugILFrame::GetArgument 方法</span><span class="sxs-lookup"><span data-stu-id="5cf17-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="5cf17-103">在此 Microsoft intermediate language (MSIL) 堆疊框架中取得指定的引數的值。</span><span class="sxs-lookup"><span data-stu-id="5cf17-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf17-104">語法</span><span class="sxs-lookup"><span data-stu-id="5cf17-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cf17-105">參數</span><span class="sxs-lookup"><span data-stu-id="5cf17-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="5cf17-106">[in]在此 MSIL 堆疊框架的引數的索引。</span><span class="sxs-lookup"><span data-stu-id="5cf17-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5cf17-107">[out]ICorDebugValue 物件，表示擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5cf17-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cf17-108">備註</span><span class="sxs-lookup"><span data-stu-id="5cf17-108">Remarks</span></span>  
 <span data-ttu-id="5cf17-109">`GetArgument`方法可以用在 MSIL 堆疊框架中或在 just-in-time (JIT) 編譯過的框架中。</span><span class="sxs-lookup"><span data-stu-id="5cf17-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cf17-110">需求</span><span class="sxs-lookup"><span data-stu-id="5cf17-110">Requirements</span></span>  
 <span data-ttu-id="5cf17-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5cf17-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf17-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cf17-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cf17-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cf17-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cf17-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf17-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
