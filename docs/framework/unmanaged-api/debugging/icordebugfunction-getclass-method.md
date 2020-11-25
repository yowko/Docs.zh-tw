---
title: ICorDebugFunction::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 40cb59a2ad0539764702369b13d632eddbab8174
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728156"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="89d0e-102">ICorDebugFunction::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="89d0e-102">ICorDebugFunction::GetClass Method</span></span>

<span data-ttu-id="89d0e-103">取得 ICorDebugClass 物件，這個物件表示此函式所屬的類別。</span><span class="sxs-lookup"><span data-stu-id="89d0e-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="89d0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89d0e-105">參數</span><span class="sxs-lookup"><span data-stu-id="89d0e-105">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="89d0e-106">擴展代表類別之物件位址的指標 `ICorDebugClass` ，如果此函式不是類別的成員，則為 null。</span><span class="sxs-lookup"><span data-stu-id="89d0e-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89d0e-107">需求</span><span class="sxs-lookup"><span data-stu-id="89d0e-107">Requirements</span></span>  

 <span data-ttu-id="89d0e-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89d0e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d0e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89d0e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89d0e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89d0e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89d0e-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d0e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
