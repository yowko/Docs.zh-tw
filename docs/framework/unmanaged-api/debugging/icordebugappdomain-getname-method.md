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
ms.openlocfilehash: 3db37576f5da7b26e7bd9d3343f8bb8b97f2ba82
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895237"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="43120-102">ICorDebugAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="43120-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="43120-103">取得應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="43120-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43120-104">語法</span><span class="sxs-lookup"><span data-stu-id="43120-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43120-105">參數</span><span class="sxs-lookup"><span data-stu-id="43120-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="43120-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="43120-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="43120-107">將此值設定為零，以將此方法置於查詢模式。</span><span class="sxs-lookup"><span data-stu-id="43120-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="43120-108">脫銷名稱大小的指標，或中`szName`實際傳回的字元數。</span><span class="sxs-lookup"><span data-stu-id="43120-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="43120-109">在查詢模式中，此值可讓呼叫者知道要為名稱配置的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="43120-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="43120-110">脫銷儲存應用程式功能變數名稱稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="43120-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43120-111">備註</span><span class="sxs-lookup"><span data-stu-id="43120-111">Remarks</span></span>  
 <span data-ttu-id="43120-112">偵錯工具會呼叫`GetName`方法一次，以取得名稱所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="43120-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="43120-113">偵錯工具會配置緩衝區，然後第二次呼叫方法來填滿緩衝區。</span><span class="sxs-lookup"><span data-stu-id="43120-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="43120-114">第一次呼叫，以取得名稱的大小，稱為「*查詢模式*」。</span><span class="sxs-lookup"><span data-stu-id="43120-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43120-115">需求</span><span class="sxs-lookup"><span data-stu-id="43120-115">Requirements</span></span>  
 <span data-ttu-id="43120-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43120-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43120-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43120-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43120-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43120-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43120-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43120-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
