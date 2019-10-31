---
title: ICorDebugVariableHome：： GetCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: 4770eb3e93104dd3862eb2163faf1dc7fe9008ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125141"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="7a2cc-102">ICorDebugVariableHome：： GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="7a2cc-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="7a2cc-103">取得包含這個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)物件的 "ICorDebugCode" 實例。</span><span class="sxs-lookup"><span data-stu-id="7a2cc-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a2cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a2cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a2cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a2cc-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7a2cc-106">脫銷包含這個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)物件之 "ICorDebugCode" 實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="7a2cc-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a2cc-107">需求</span><span class="sxs-lookup"><span data-stu-id="7a2cc-107">Requirements</span></span>  
 <span data-ttu-id="7a2cc-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a2cc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a2cc-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a2cc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a2cc-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a2cc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a2cc-111">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a2cc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2cc-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a2cc-112">See also</span></span>

- [<span data-ttu-id="7a2cc-113">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="7a2cc-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
