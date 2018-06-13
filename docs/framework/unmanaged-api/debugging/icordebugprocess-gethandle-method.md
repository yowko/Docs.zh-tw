---
title: ICorDebugProcess::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60bd7567f541a0bbaa3591d2f2905d13064dec3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423438"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="730fb-102">ICorDebugProcess::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="730fb-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="730fb-103">取得處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="730fb-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="730fb-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="730fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="730fb-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="730fb-106">[out]指標`HPROCESS`也就是處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="730fb-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="730fb-107">備註</span><span class="sxs-lookup"><span data-stu-id="730fb-107">Remarks</span></span>  
 <span data-ttu-id="730fb-108">擷取控制代碼的擁有者偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="730fb-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="730fb-109">偵錯工具應該重複的控制代碼後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="730fb-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730fb-110">需求</span><span class="sxs-lookup"><span data-stu-id="730fb-110">Requirements</span></span>  
 <span data-ttu-id="730fb-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="730fb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730fb-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="730fb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="730fb-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="730fb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="730fb-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730fb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
