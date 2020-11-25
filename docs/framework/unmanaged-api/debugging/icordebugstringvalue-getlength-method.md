---
title: ICorDebugStringValue::GetLength 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: 74a4b42be09c577cc80f1a73e077694e5a4a8d5f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697112"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="ba701-102">ICorDebugStringValue::GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="ba701-102">ICorDebugStringValue::GetLength Method</span></span>

<span data-ttu-id="ba701-103">取得此 ICorDebugStringValue 所參考之字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="ba701-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba701-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba701-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba701-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba701-105">Parameters</span></span>  

 `pcchString`  
 <span data-ttu-id="ba701-106">擴展值的指標，指定此物件所參考之字串的長度 `ICorDebugStringValue` 。</span><span class="sxs-lookup"><span data-stu-id="ba701-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba701-107">需求</span><span class="sxs-lookup"><span data-stu-id="ba701-107">Requirements</span></span>  

 <span data-ttu-id="ba701-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba701-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba701-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba701-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba701-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba701-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba701-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba701-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
