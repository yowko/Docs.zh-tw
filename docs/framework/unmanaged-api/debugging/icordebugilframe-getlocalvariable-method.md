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
ms.openlocfilehash: 3424646337c3f90f15d991f3f669a296bf11d8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413003"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="ba6b7-102">ICorDebugILFrame::GetLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="ba6b7-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="ba6b7-103">此 Microsoft intermediate language (MSIL) 堆疊框架中取得指定的本機變數的值。</span><span class="sxs-lookup"><span data-stu-id="ba6b7-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba6b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba6b7-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba6b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba6b7-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="ba6b7-106">[in]在這個 MSIL 堆疊框架中區域變數的索引。</span><span class="sxs-lookup"><span data-stu-id="ba6b7-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ba6b7-107">[out]ICorDebugValue 物件，代表擷取的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="ba6b7-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba6b7-108">備註</span><span class="sxs-lookup"><span data-stu-id="ba6b7-108">Remarks</span></span>  
 <span data-ttu-id="ba6b7-109">`GetLocalVariable`方法可以用在 MSIL 堆疊框架中或在 just-in-time (JIT) 編譯的框架中。</span><span class="sxs-lookup"><span data-stu-id="ba6b7-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba6b7-110">需求</span><span class="sxs-lookup"><span data-stu-id="ba6b7-110">Requirements</span></span>  
 <span data-ttu-id="ba6b7-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba6b7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba6b7-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba6b7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba6b7-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba6b7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba6b7-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba6b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
