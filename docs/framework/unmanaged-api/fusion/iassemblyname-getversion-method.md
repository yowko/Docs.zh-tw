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
ms.openlocfilehash: a28cb9f1fd2e12cd750d4eeb8db6c2d7a181b414
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197421"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="ec866-102">IAssemblyName::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="ec866-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="ec866-103">取得所參考的組件的版本資訊[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="ec866-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec866-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec866-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec866-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec866-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="ec866-106">[out]高 32 位元的版本。</span><span class="sxs-lookup"><span data-stu-id="ec866-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="ec866-107">[out]低 32 位元的版本。</span><span class="sxs-lookup"><span data-stu-id="ec866-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec866-108">需求</span><span class="sxs-lookup"><span data-stu-id="ec866-108">Requirements</span></span>  
 <span data-ttu-id="ec866-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec866-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec866-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ec866-110">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="ec866-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ec866-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec866-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec866-112">See also</span></span>

- [<span data-ttu-id="ec866-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="ec866-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
