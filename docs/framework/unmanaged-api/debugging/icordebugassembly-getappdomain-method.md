---
title: ICorDebugAssembly::GetAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 81936052c3fa2ad4fb77b503341b8b4873b80695
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894938"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="55709-102">ICorDebugAssembly::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="55709-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="55709-103">取得包含這個`ICorDebugAssembly`實例之應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="55709-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55709-104">語法</span><span class="sxs-lookup"><span data-stu-id="55709-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55709-105">參數</span><span class="sxs-lookup"><span data-stu-id="55709-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="55709-106">脫銷代表應用程式域之 ICorDebugAppDomain 介面位址的指標。</span><span class="sxs-lookup"><span data-stu-id="55709-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55709-107">備註</span><span class="sxs-lookup"><span data-stu-id="55709-107">Remarks</span></span>  
 <span data-ttu-id="55709-108">如果這個元件是系統元件， `GetAppDomain`則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="55709-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55709-109">需求</span><span class="sxs-lookup"><span data-stu-id="55709-109">Requirements</span></span>  
 <span data-ttu-id="55709-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55709-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55709-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55709-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55709-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55709-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55709-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55709-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
