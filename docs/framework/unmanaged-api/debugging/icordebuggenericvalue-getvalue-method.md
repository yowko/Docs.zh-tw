---
title: ICorDebugGenericValue::GetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: dd1c1ba4a976a10d0c38c5295fff838faf072f51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728104"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="624b2-102">ICorDebugGenericValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="624b2-102">ICorDebugGenericValue::GetValue Method</span></span>

<span data-ttu-id="624b2-103">將這個泛型的值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="624b2-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="624b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="624b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="624b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="624b2-105">Parameters</span></span>  

 `pTo`  
 <span data-ttu-id="624b2-106">擴展這個 ICorDebugGenericValue 物件所表示之值的指標。</span><span class="sxs-lookup"><span data-stu-id="624b2-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="624b2-107">值可以是簡單類型或參考型別 (也就是指標) 。</span><span class="sxs-lookup"><span data-stu-id="624b2-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="624b2-108">需求</span><span class="sxs-lookup"><span data-stu-id="624b2-108">Requirements</span></span>  

 <span data-ttu-id="624b2-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="624b2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="624b2-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="624b2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="624b2-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="624b2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="624b2-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="624b2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
