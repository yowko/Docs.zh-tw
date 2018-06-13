---
title: ICorDebugHandleValue::Dispose 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9114799b87d39333ff9da66429dc1ea99ec2131c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413426"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="0e1ea-102">ICorDebugHandleValue::Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="0e1ea-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="0e1ea-103">釋放這個 ICorDebugHandleValue 物件所參考但未明確地釋放的介面指標的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e1ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e1ea-104">Syntax</span></span>  
  
```  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0e1ea-105">需求</span><span class="sxs-lookup"><span data-stu-id="0e1ea-105">Requirements</span></span>  
 <span data-ttu-id="0e1ea-106">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e1ea-107">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e1ea-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e1ea-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e1ea-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e1ea-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e1ea-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
