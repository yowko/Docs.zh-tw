---
title: ICorDebugThread::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52962ea7d2cf3dd1822b1a36cc6cfcb56bc427f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417189"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="4a576-102">ICorDebugThread::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="4a576-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="4a576-103">取得此 ICorDebugThread 的使用中部分的目前作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="4a576-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a576-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a576-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a576-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a576-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="4a576-106">[out]執行緒的識別項。</span><span class="sxs-lookup"><span data-stu-id="4a576-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a576-107">備註</span><span class="sxs-lookup"><span data-stu-id="4a576-107">Remarks</span></span>  
 <span data-ttu-id="4a576-108">作業系統識別項期間執行的處理序中，有可能變更，而且可以對不同的執行緒不同的值。</span><span class="sxs-lookup"><span data-stu-id="4a576-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a576-109">需求</span><span class="sxs-lookup"><span data-stu-id="4a576-109">Requirements</span></span>  
 <span data-ttu-id="4a576-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a576-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a576-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a576-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a576-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a576-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a576-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a576-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
