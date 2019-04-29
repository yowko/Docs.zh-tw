---
title: ICorDebugChain::EnumerateFrames 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568f8ca3b92ef465ab595348f68895f389d61e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645314"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="41d10-102">ICorDebugChain::EnumerateFrames 方法</span><span class="sxs-lookup"><span data-stu-id="41d10-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="41d10-103">取得列舉值，其中包含所有的受管理的堆疊框架，在鏈結中，從最新的框架開始。</span><span class="sxs-lookup"><span data-stu-id="41d10-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d10-104">語法</span><span class="sxs-lookup"><span data-stu-id="41d10-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d10-105">參數</span><span class="sxs-lookup"><span data-stu-id="41d10-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="41d10-106">[out]ICorDebugFrameEnum 的堆疊框架的列舉值物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="41d10-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41d10-107">備註</span><span class="sxs-lookup"><span data-stu-id="41d10-107">Remarks</span></span>  
 <span data-ttu-id="41d10-108">鏈結代表執行緒的實體呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="41d10-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="41d10-109">`EnumerateFrames`方法應該呼叫只會針對受管理的鏈結。</span><span class="sxs-lookup"><span data-stu-id="41d10-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="41d10-110">偵錯 API 並未提供方法以取得包含在未受管理的鏈結中的框架。</span><span class="sxs-lookup"><span data-stu-id="41d10-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="41d10-111">偵錯工具必須使用其他方法來取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="41d10-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d10-112">需求</span><span class="sxs-lookup"><span data-stu-id="41d10-112">Requirements</span></span>  
 <span data-ttu-id="41d10-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41d10-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d10-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41d10-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41d10-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41d10-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41d10-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d10-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
