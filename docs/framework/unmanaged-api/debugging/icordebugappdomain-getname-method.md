---
title: ICorDebugAppDomain::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179082"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="ff961-102">ICorDebugAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="ff961-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="ff961-103">獲取應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff961-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff961-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff961-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff961-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff961-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ff961-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ff961-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="ff961-107">將此值設置為零，以將此方法置於查詢模式。</span><span class="sxs-lookup"><span data-stu-id="ff961-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ff961-108">[出]指向名稱大小或 中`szName`實際返回的字元數的指標。</span><span class="sxs-lookup"><span data-stu-id="ff961-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="ff961-109">在查詢模式下，此值允許調用方知道要為名稱分配緩衝區有多大。</span><span class="sxs-lookup"><span data-stu-id="ff961-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ff961-110">[出]存儲應用程式功能變數名稱稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="ff961-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff961-111">備註</span><span class="sxs-lookup"><span data-stu-id="ff961-111">Remarks</span></span>  
 <span data-ttu-id="ff961-112">調試器調用`GetName`該方法一次，以獲得名稱所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="ff961-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="ff961-113">調試器分配緩衝區，然後第二次調用 該方法以填充緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ff961-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="ff961-114">第一個調用（獲取名稱的大小）稱為*查詢模式*。</span><span class="sxs-lookup"><span data-stu-id="ff961-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff961-115">需求</span><span class="sxs-lookup"><span data-stu-id="ff961-115">Requirements</span></span>  
 <span data-ttu-id="ff961-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff961-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff961-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff961-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff961-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff961-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff961-119">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff961-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
