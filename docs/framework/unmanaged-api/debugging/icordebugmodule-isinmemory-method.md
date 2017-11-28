---
title: "ICorDebugModule::IsInMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsInMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58f7964faee19f85c83d1b9b1c3e176354ae9588
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="e4054-102">ICorDebugModule::IsInMemory 方法</span><span class="sxs-lookup"><span data-stu-id="e4054-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="e4054-103">取得值，指出是否此模組只存在於記憶體。</span><span class="sxs-lookup"><span data-stu-id="e4054-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4054-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4054-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4054-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4054-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="e4054-106">[out]`true`如果此模組只存在於記憶體中; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="e4054-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4054-107">備註</span><span class="sxs-lookup"><span data-stu-id="e4054-107">Remarks</span></span>  
 <span data-ttu-id="e4054-108">Common language runtime (CLR) 支援的載入模組，從原始資料流的位元組。</span><span class="sxs-lookup"><span data-stu-id="e4054-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="e4054-109">這類模組稱為*記憶體中模組*並不存在於磁碟上。</span><span class="sxs-lookup"><span data-stu-id="e4054-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4054-110">需求</span><span class="sxs-lookup"><span data-stu-id="e4054-110">Requirements</span></span>  
 <span data-ttu-id="e4054-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4054-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4054-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4054-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4054-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4054-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4054-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4054-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4054-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4054-115">See Also</span></span>  
    
 
