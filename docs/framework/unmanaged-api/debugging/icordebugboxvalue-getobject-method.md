---
title: ICorDebugBoxValue::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: df151e9fc89214d0851ebe60c7ebdb87224f880c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719069"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="d5cd0-102">ICorDebugBoxValue::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="d5cd0-102">ICorDebugBoxValue::GetObject Method</span></span>

<span data-ttu-id="d5cd0-103">取得已裝箱的值。</span><span class="sxs-lookup"><span data-stu-id="d5cd0-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5cd0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5cd0-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5cd0-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="d5cd0-106">擴展ICorDebugObjectValue 物件位址的指標，該物件表示已框出的值。</span><span class="sxs-lookup"><span data-stu-id="d5cd0-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cd0-107">需求</span><span class="sxs-lookup"><span data-stu-id="d5cd0-107">Requirements</span></span>  

 <span data-ttu-id="d5cd0-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5cd0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cd0-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5cd0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5cd0-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5cd0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5cd0-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cd0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
