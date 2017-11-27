---
title: "ICorDebugAppDomain::GetName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590bfb5d7d8cac8e322bddfe6258ad9bf377dad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="06fe5-102">ICorDebugAppDomain::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="06fe5-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="06fe5-103">取得應用程式定義域的名稱。</span><span class="sxs-lookup"><span data-stu-id="06fe5-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fe5-104">語法</span><span class="sxs-lookup"><span data-stu-id="06fe5-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06fe5-105">參數</span><span class="sxs-lookup"><span data-stu-id="06fe5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="06fe5-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="06fe5-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="06fe5-107">設定此值為零可放在查詢模式中這個方法。</span><span class="sxs-lookup"><span data-stu-id="06fe5-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="06fe5-108">[out]名稱或中實際傳回的字元數的大小的指標`szName`。</span><span class="sxs-lookup"><span data-stu-id="06fe5-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="06fe5-109">在查詢模式中，這個值會讓呼叫者知道如何多大的緩衝區配置的名稱。</span><span class="sxs-lookup"><span data-stu-id="06fe5-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="06fe5-110">[out]陣列，其中會儲存在應用程式定義域的名稱。</span><span class="sxs-lookup"><span data-stu-id="06fe5-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06fe5-111">備註</span><span class="sxs-lookup"><span data-stu-id="06fe5-111">Remarks</span></span>  
 <span data-ttu-id="06fe5-112">偵錯工具呼叫`GetName`方法一次，若要取得之名稱所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="06fe5-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="06fe5-113">偵錯工具會配置緩衝區，然後再呼叫第二次方法來填滿緩衝區。</span><span class="sxs-lookup"><span data-stu-id="06fe5-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="06fe5-114">第一次呼叫，以取得名稱的大小指*查詢模式*。</span><span class="sxs-lookup"><span data-stu-id="06fe5-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fe5-115">需求</span><span class="sxs-lookup"><span data-stu-id="06fe5-115">Requirements</span></span>  
 <span data-ttu-id="06fe5-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06fe5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06fe5-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06fe5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06fe5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06fe5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06fe5-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06fe5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
