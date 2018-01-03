---
title: "IAssemblyName::GetName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 681df0b4d6b3d7206954264355afb3ef2628243d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="b2e16-102">IAssemblyName::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="b2e16-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="b2e16-103">取得所參考的組件的簡單、 未加密名稱[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="b2e16-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e16-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2e16-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2e16-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2e16-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="b2e16-106">[in、 out]大小`pwzName`寬字元，包括 null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="b2e16-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="b2e16-107">[out]緩衝區來保存參考的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2e16-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e16-108">需求</span><span class="sxs-lookup"><span data-stu-id="b2e16-108">Requirements</span></span>  
 <span data-ttu-id="b2e16-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2e16-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2e16-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b2e16-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b2e16-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2e16-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e16-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e16-112">See Also</span></span>  
 [<span data-ttu-id="b2e16-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="b2e16-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
