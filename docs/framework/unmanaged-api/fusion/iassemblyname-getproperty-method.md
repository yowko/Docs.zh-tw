---
title: IAssemblyName::GetProperty 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9af0773c2ef066c103f823e4d28c0fd6e9eadc24
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086555"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="0a18a-102">IAssemblyName::GetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="0a18a-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="0a18a-103">取得指定的屬性識別碼所參考之屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="0a18a-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a18a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a18a-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a18a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a18a-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="0a18a-106">[in]要求屬性的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="0a18a-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="0a18a-107">[out]傳回的屬性的資料。</span><span class="sxs-lookup"><span data-stu-id="0a18a-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="0a18a-108">[in、 out]大小，以位元組為單位的`pvProperty`。</span><span class="sxs-lookup"><span data-stu-id="0a18a-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a18a-109">需求</span><span class="sxs-lookup"><span data-stu-id="0a18a-109">Requirements</span></span>  
 <span data-ttu-id="0a18a-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a18a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a18a-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0a18a-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="0a18a-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0a18a-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a18a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a18a-113">See also</span></span>

- [<span data-ttu-id="0a18a-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="0a18a-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
