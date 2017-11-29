---
title: "ICorDebugEnum::GetCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum.GetCount
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bca3631f9c7a8f6ec3d145f8573241642cb1b1c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="a137c-102">ICorDebugEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="a137c-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="a137c-103">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="a137c-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a137c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a137c-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a137c-105">參數</span><span class="sxs-lookup"><span data-stu-id="a137c-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="a137c-106">[out]列舉中的項目編號的指標。</span><span class="sxs-lookup"><span data-stu-id="a137c-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a137c-107">需求</span><span class="sxs-lookup"><span data-stu-id="a137c-107">Requirements</span></span>  
 <span data-ttu-id="a137c-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a137c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a137c-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a137c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a137c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a137c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a137c-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a137c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
