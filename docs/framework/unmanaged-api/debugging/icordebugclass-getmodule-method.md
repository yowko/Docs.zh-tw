---
title: ICorDebugClass::GetModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: e95d10512da73d9f483b87557fd7cd4574503c70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728455"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="0de55-102">ICorDebugClass::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="0de55-102">ICorDebugClass::GetModule Method</span></span>

<span data-ttu-id="0de55-103">取得定義這個類別的模組。</span><span class="sxs-lookup"><span data-stu-id="0de55-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de55-104">語法</span><span class="sxs-lookup"><span data-stu-id="0de55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de55-105">參數</span><span class="sxs-lookup"><span data-stu-id="0de55-105">Parameters</span></span>  

 `pModule`  
 <span data-ttu-id="0de55-106">擴展ICorDebugModule 物件位址的指標，該物件表示定義此類別的模組。</span><span class="sxs-lookup"><span data-stu-id="0de55-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de55-107">需求</span><span class="sxs-lookup"><span data-stu-id="0de55-107">Requirements</span></span>  

 <span data-ttu-id="0de55-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0de55-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de55-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0de55-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0de55-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0de55-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0de55-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de55-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
