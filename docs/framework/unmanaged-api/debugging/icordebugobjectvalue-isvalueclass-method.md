---
title: "ICorDebugObjectValue::IsValueClass 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.IsValueClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f398de277a334a2666a12eacf6727674aed8755
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="b6485-102">ICorDebugObjectValue::IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="b6485-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="b6485-103">取得值，指出這個物件的值是否為實值類型。</span><span class="sxs-lookup"><span data-stu-id="b6485-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6485-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6485-104">Syntax</span></span>  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6485-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6485-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="b6485-106">[out]為的布林值的指標`true`這個 「 ICorDebugObjectValue"所代表的物件值，是實值類型，而不是參考類型; 如果否則`pbIsValueClass`是`false`。</span><span class="sxs-lookup"><span data-stu-id="b6485-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6485-107">需求</span><span class="sxs-lookup"><span data-stu-id="b6485-107">Requirements</span></span>  
 <span data-ttu-id="b6485-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6485-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6485-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6485-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6485-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6485-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6485-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6485-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6485-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6485-112">See Also</span></span>  
    
 
