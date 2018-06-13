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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6d30a9f03d8717486be7cd89bb182d350a82df7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411632"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="0d484-102">ICorDebugGenericValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="0d484-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="0d484-103">將此泛型的值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0d484-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d484-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d484-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d484-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d484-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="0d484-106">[out]這個 ICorDebugGenericValue 物件所表示之值的指標。</span><span class="sxs-lookup"><span data-stu-id="0d484-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="0d484-107">值可能是簡單類型或參考類型 （也就是指標）。</span><span class="sxs-lookup"><span data-stu-id="0d484-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d484-108">需求</span><span class="sxs-lookup"><span data-stu-id="0d484-108">Requirements</span></span>  
 <span data-ttu-id="0d484-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d484-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d484-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d484-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d484-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d484-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d484-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d484-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
