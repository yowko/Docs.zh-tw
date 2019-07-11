---
title: IAssemblyName::GetVersion 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5b5f7ce6a4ce8f542b3c49fe4749bfde23ecf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744497"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="e09a0-102">IAssemblyName::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="e09a0-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="e09a0-103">取得所參考的組件的版本資訊[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="e09a0-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e09a0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e09a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="e09a0-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="e09a0-106">[out]高 32 位元的版本。</span><span class="sxs-lookup"><span data-stu-id="e09a0-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="e09a0-107">[out]低 32 位元的版本。</span><span class="sxs-lookup"><span data-stu-id="e09a0-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e09a0-108">需求</span><span class="sxs-lookup"><span data-stu-id="e09a0-108">Requirements</span></span>  
 <span data-ttu-id="e09a0-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e09a0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e09a0-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e09a0-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e09a0-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e09a0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09a0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e09a0-112">See also</span></span>

- [<span data-ttu-id="e09a0-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="e09a0-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
