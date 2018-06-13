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
ms.openlocfilehash: ee16193c95c9e754f5bff9aeaf37ff74c456891e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428464"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="5d718-102">IAssemblyName::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="5d718-102">IAssemblyName::Clone Method</span></span>
<span data-ttu-id="5d718-103">建立這樣的淺層複本[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="5d718-103">Creates a shallow copy of this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d718-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d718-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d718-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d718-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="5d718-106">[out]這個傳回的複本`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="5d718-106">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d718-107">需求</span><span class="sxs-lookup"><span data-stu-id="5d718-107">Requirements</span></span>  
 <span data-ttu-id="5d718-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d718-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d718-109">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5d718-109">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5d718-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d718-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d718-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d718-111">See Also</span></span>  
 [<span data-ttu-id="5d718-112">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="5d718-112">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
