---
title: "ICorDebugHandleValue::Dispose 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue.Dispose
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 626b5c1f9bb43f1853a4052dc170c674b7644954
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="93de3-102">ICorDebugHandleValue::Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="93de3-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="93de3-103">釋放這個 ICorDebugHandleValue 物件所參考但未明確地釋放的介面指標的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="93de3-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93de3-104">語法</span><span class="sxs-lookup"><span data-stu-id="93de3-104">Syntax</span></span>  
  
```  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="93de3-105">需求</span><span class="sxs-lookup"><span data-stu-id="93de3-105">Requirements</span></span>  
 <span data-ttu-id="93de3-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93de3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93de3-107">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93de3-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93de3-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93de3-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93de3-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93de3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
