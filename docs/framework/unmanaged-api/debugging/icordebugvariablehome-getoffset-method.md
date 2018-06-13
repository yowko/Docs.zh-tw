---
title: ICorDebugVariableHome::GetOffset 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a2ea7273fec62654c168d6786d3644b184ff7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419565"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="5a8e1-102">ICorDebugVariableHome::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="5a8e1-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="5a8e1-103">取得從基底暫存器變數位移。</span><span class="sxs-lookup"><span data-stu-id="5a8e1-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a8e1-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a8e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a8e1-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="5a8e1-106">[out]基底暫存器從位移。</span><span class="sxs-lookup"><span data-stu-id="5a8e1-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a8e1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a8e1-107">Return Value</span></span>  
 <span data-ttu-id="5a8e1-108">方法會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="5a8e1-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="5a8e1-109">值</span><span class="sxs-lookup"><span data-stu-id="5a8e1-109">Value</span></span>|<span data-ttu-id="5a8e1-110">描述</span><span class="sxs-lookup"><span data-stu-id="5a8e1-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="5a8e1-111">變數是在暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="5a8e1-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="5a8e1-112">變數不是在暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="5a8e1-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a8e1-113">需求</span><span class="sxs-lookup"><span data-stu-id="5a8e1-113">Requirements</span></span>  
 <span data-ttu-id="5a8e1-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8e1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a8e1-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a8e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a8e1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a8e1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a8e1-117">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a8e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8e1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a8e1-118">See Also</span></span>  
 [<span data-ttu-id="5a8e1-119">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="5a8e1-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
