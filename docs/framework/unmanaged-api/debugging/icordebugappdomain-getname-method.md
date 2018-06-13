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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405765"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="9c43b-102">ICorDebugAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="9c43b-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="9c43b-103">取得應用程式定義域的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c43b-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c43b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c43b-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c43b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c43b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9c43b-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="9c43b-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="9c43b-107">設定此值為零可放在查詢模式中這個方法。</span><span class="sxs-lookup"><span data-stu-id="9c43b-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9c43b-108">[out]名稱或中實際傳回的字元數的大小的指標`szName`。</span><span class="sxs-lookup"><span data-stu-id="9c43b-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="9c43b-109">在查詢模式中，這個值會讓呼叫者知道如何多大的緩衝區配置的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c43b-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9c43b-110">[out]陣列，其中會儲存在應用程式定義域的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c43b-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c43b-111">備註</span><span class="sxs-lookup"><span data-stu-id="9c43b-111">Remarks</span></span>  
 <span data-ttu-id="9c43b-112">偵錯工具呼叫`GetName`方法一次，若要取得之名稱所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="9c43b-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="9c43b-113">偵錯工具會配置緩衝區，然後再呼叫第二次方法來填滿緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9c43b-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="9c43b-114">第一次呼叫，以取得名稱的大小指*查詢模式*。</span><span class="sxs-lookup"><span data-stu-id="9c43b-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c43b-115">需求</span><span class="sxs-lookup"><span data-stu-id="9c43b-115">Requirements</span></span>  
 <span data-ttu-id="9c43b-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c43b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c43b-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c43b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c43b-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c43b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c43b-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c43b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
