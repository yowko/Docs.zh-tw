---
title: "ICorDebugVariableHome::GetArgumentIndex 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetArgumentIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 175e45758d26d8168279c825d41ee58d049edf0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="d2a03-102">ICorDebugVariableHome::GetArgumentIndex 方法</span><span class="sxs-lookup"><span data-stu-id="d2a03-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="d2a03-103">取得函式引數索引。</span><span class="sxs-lookup"><span data-stu-id="d2a03-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a03-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2a03-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2a03-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2a03-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="d2a03-106">[out]引數索引指標。</span><span class="sxs-lookup"><span data-stu-id="d2a03-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2a03-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2a03-107">Return Value</span></span>  
 <span data-ttu-id="d2a03-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="d2a03-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d2a03-109">值</span><span class="sxs-lookup"><span data-stu-id="d2a03-109">Value</span></span>|<span data-ttu-id="d2a03-110">說明</span><span class="sxs-lookup"><span data-stu-id="d2a03-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d2a03-111">方法呼叫傳回有效的引數索引。</span><span class="sxs-lookup"><span data-stu-id="d2a03-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d2a03-112">目前[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)的執行個體表示的本機變數。</span><span class="sxs-lookup"><span data-stu-id="d2a03-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2a03-113">備註</span><span class="sxs-lookup"><span data-stu-id="d2a03-113">Remarks</span></span>  
 <span data-ttu-id="d2a03-114">引數索引可以用來擷取中繼資料，這個引數。</span><span class="sxs-lookup"><span data-stu-id="d2a03-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a03-115">需求</span><span class="sxs-lookup"><span data-stu-id="d2a03-115">Requirements</span></span>  
 <span data-ttu-id="d2a03-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a03-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a03-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2a03-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2a03-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2a03-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2a03-119">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a03-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a03-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2a03-120">See Also</span></span>  
 [<span data-ttu-id="d2a03-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="d2a03-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
