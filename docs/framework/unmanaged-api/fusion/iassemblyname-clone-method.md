---
title: IAssemblyName::Clone 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c824874d340aa3d381b3340408021ef1ed7eec6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166695"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="161b5-102">IAssemblyName::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="161b5-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="161b5-103">建立這個的淺層複製[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="161b5-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="161b5-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="161b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="161b5-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="161b5-106">[out]這個傳回的複本`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="161b5-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161b5-107">需求</span><span class="sxs-lookup"><span data-stu-id="161b5-107">Requirements</span></span>  
 <span data-ttu-id="161b5-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="161b5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161b5-109">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="161b5-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="161b5-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161b5-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161b5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="161b5-111">See also</span></span>

- [<span data-ttu-id="161b5-112">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="161b5-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
