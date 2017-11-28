---
title: "IAssemblyName::SetProperty 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.SetProperty
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b99b9c01d014f7b6c02eedde157fa6fdd4e142a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="b0038-102">IAssemblyName::SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="b0038-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="b0038-103">設定指定的屬性的識別項所參考之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b0038-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0038-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0038-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0038-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0038-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="b0038-106">[in]屬性會設定其值唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="b0038-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="b0038-107">[in]要用來設定所參考之屬性的值`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="b0038-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="b0038-108">[in]大小，以位元組為單位的`pvProperty`。</span><span class="sxs-lookup"><span data-stu-id="b0038-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0038-109">需求</span><span class="sxs-lookup"><span data-stu-id="b0038-109">Requirements</span></span>  
 <span data-ttu-id="b0038-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0038-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0038-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b0038-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b0038-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0038-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0038-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0038-113">See Also</span></span>  
 [<span data-ttu-id="b0038-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="b0038-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
