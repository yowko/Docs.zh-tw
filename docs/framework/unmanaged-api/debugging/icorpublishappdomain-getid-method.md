---
title: "ICorPublishAppDomain::GetID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfbde806f409f2639b2468e0ba962b1659d1ffc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="0f808-102">ICorPublishAppDomain::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="0f808-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="0f808-103">取得這個唯一識別碼[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="0f808-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f808-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f808-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f808-105">參數</span><span class="sxs-lookup"><span data-stu-id="0f808-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="0f808-106">[out]應用程式定義域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="0f808-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f808-107">備註</span><span class="sxs-lookup"><span data-stu-id="0f808-107">Remarks</span></span>  
 <span data-ttu-id="0f808-108">只能在包含處理序的範圍中是唯一的識別項。</span><span class="sxs-lookup"><span data-stu-id="0f808-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f808-109">需求</span><span class="sxs-lookup"><span data-stu-id="0f808-109">Requirements</span></span>  
 <span data-ttu-id="0f808-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f808-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f808-111">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="0f808-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0f808-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f808-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f808-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f808-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f808-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f808-114">See Also</span></span>  
 [<span data-ttu-id="0f808-115">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="0f808-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
