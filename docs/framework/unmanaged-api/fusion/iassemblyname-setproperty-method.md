---
title: IAssemblyName::SetProperty 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cc2a2c7991eb4d11873ebb6a2df92ccc45cde9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697221"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="ea1f1-102">IAssemblyName::SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="ea1f1-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="ea1f1-103">設定指定的屬性識別碼所參考之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea1f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea1f1-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea1f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea1f1-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="ea1f1-106">[in]將設定其值之屬性的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="ea1f1-107">[in]要用來設定所參考之屬性的值`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="ea1f1-108">[in]大小，以位元組為單位的`pvProperty`。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea1f1-109">需求</span><span class="sxs-lookup"><span data-stu-id="ea1f1-109">Requirements</span></span>  
 <span data-ttu-id="ea1f1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea1f1-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ea1f1-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ea1f1-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea1f1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1f1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea1f1-113">See also</span></span>

- [<span data-ttu-id="ea1f1-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="ea1f1-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
