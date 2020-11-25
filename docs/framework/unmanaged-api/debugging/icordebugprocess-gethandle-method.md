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
ms.openlocfilehash: 87b7b7381ef53f7e2abebc053b5c9f87f94d96c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695058"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="dc10a-102">ICorDebugProcess::GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="dc10a-102">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="dc10a-103">取得進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="dc10a-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc10a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc10a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc10a-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc10a-105">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="dc10a-106">擴展指向 `HPROCESS` 進程控制碼之的指標。</span><span class="sxs-lookup"><span data-stu-id="dc10a-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc10a-107">備註</span><span class="sxs-lookup"><span data-stu-id="dc10a-107">Remarks</span></span>  

 <span data-ttu-id="dc10a-108">取出的控制碼是由偵錯工具所擁有。</span><span class="sxs-lookup"><span data-stu-id="dc10a-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="dc10a-109">偵錯工具應該在使用之前複製控制碼。</span><span class="sxs-lookup"><span data-stu-id="dc10a-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc10a-110">需求</span><span class="sxs-lookup"><span data-stu-id="dc10a-110">Requirements</span></span>  

 <span data-ttu-id="dc10a-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc10a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc10a-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc10a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc10a-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc10a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc10a-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc10a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
