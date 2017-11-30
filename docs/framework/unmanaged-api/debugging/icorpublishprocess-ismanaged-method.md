---
title: "ICorPublishProcess::IsManaged 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 622781a6c1ad5d5efa3bb2d5227c4f5b845bf94e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="dc4bf-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="dc4bf-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="dc4bf-103">取得值，指出是否處理程序參考這個[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)稱為具有 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc4bf-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc4bf-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc4bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc4bf-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="dc4bf-106">[out]布林值，指出是否處理具有 managed 程式碼指標。</span><span class="sxs-lookup"><span data-stu-id="dc4bf-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="dc4bf-107">值是`true`如果處理程序具有 managed 程式碼; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="dc4bf-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc4bf-108">備註</span><span class="sxs-lookup"><span data-stu-id="dc4bf-108">Remarks</span></span>  
 <span data-ttu-id="dc4bf-109">因為最新版`ICorPublishProcess`只允許存取具有 managed 程式碼的處理序`IsManaged`一律會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="dc4bf-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc4bf-110">需求</span><span class="sxs-lookup"><span data-stu-id="dc4bf-110">Requirements</span></span>  
 <span data-ttu-id="dc4bf-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4bf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc4bf-112">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="dc4bf-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="dc4bf-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc4bf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc4bf-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc4bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc4bf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4bf-115">See Also</span></span>  
 [<span data-ttu-id="dc4bf-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="dc4bf-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
