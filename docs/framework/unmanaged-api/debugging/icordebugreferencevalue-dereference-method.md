---
title: ICorDebugReferenceValue::Dereference 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a0fd1981e7da5af19cf3a422c6008d373e9ac92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416588"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="d3602-102">ICorDebugReferenceValue::Dereference 方法</span><span class="sxs-lookup"><span data-stu-id="d3602-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="d3602-103">取得參考的物件。</span><span class="sxs-lookup"><span data-stu-id="d3602-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3602-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3602-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3602-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3602-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="d3602-106">[out]ICorDebugValue，表示這個 ICorDebugReferenceValue 物件指向的物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d3602-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3602-107">備註</span><span class="sxs-lookup"><span data-stu-id="d3602-107">Remarks</span></span>  
 <span data-ttu-id="d3602-108">`ICorDebugValue`物件是否有效，只在它的參考尚未停時。</span><span class="sxs-lookup"><span data-stu-id="d3602-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3602-109">需求</span><span class="sxs-lookup"><span data-stu-id="d3602-109">Requirements</span></span>  
 <span data-ttu-id="d3602-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3602-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3602-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3602-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3602-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3602-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3602-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3602-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
