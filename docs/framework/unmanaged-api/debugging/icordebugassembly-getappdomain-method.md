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
ms.openlocfilehash: 55a798bcc575aee3f309c35eb454a0675e0cbd97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734071"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="4c3f9-102">ICorDebugAssembly::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="4c3f9-102">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="4c3f9-103">取得包含此實例之應用程式域的介面指標 `ICorDebugAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="4c3f9-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c3f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="4c3f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c3f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="4c3f9-105">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="4c3f9-106">擴展代表應用程式域之 ICorDebugAppDomain 介面的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4c3f9-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c3f9-107">備註</span><span class="sxs-lookup"><span data-stu-id="4c3f9-107">Remarks</span></span>  

 <span data-ttu-id="4c3f9-108">如果這個元件是系統元件，則會傳回 `GetAppDomain` null。</span><span class="sxs-lookup"><span data-stu-id="4c3f9-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c3f9-109">需求</span><span class="sxs-lookup"><span data-stu-id="4c3f9-109">Requirements</span></span>  

 <span data-ttu-id="4c3f9-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c3f9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c3f9-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c3f9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c3f9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c3f9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c3f9-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c3f9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
