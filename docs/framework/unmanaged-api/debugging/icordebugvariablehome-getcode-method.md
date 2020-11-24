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
ms.openlocfilehash: 6f5d99e6dc4290ef69c0a0748fe15ae538e83558
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684222"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="8a610-102">ICorDebugVariableHome：： GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="8a610-102">ICorDebugVariableHome::GetCode Method</span></span>

<span data-ttu-id="8a610-103">取得包含這個 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 物件的 "ICorDebugCode" 實例。</span><span class="sxs-lookup"><span data-stu-id="8a610-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a610-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a610-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a610-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a610-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="8a610-106">擴展包含此 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 物件之 "ICorDebugCode" 實例的位址指標。</span><span class="sxs-lookup"><span data-stu-id="8a610-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a610-107">需求</span><span class="sxs-lookup"><span data-stu-id="8a610-107">Requirements</span></span>  

 <span data-ttu-id="8a610-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a610-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a610-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a610-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a610-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a610-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a610-111">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a610-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a610-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a610-112">See also</span></span>

- [<span data-ttu-id="8a610-113">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="8a610-113">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
