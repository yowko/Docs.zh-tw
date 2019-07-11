---
title: IMetaDataEmit::SetModuleProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c4e39fdbb400475d1b14639114325309ddb7597
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751036"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="9ce7e-102">IMetaDataEmit::SetModuleProps 方法</span><span class="sxs-lookup"><span data-stu-id="9ce7e-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="9ce7e-103">更新先前呼叫所定義的模組參考[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce7e-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce7e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ce7e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ce7e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9ce7e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="9ce7e-106">[in]以 Unicode 模組名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce7e-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="9ce7e-107">這是檔案名稱而不是完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce7e-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce7e-108">需求</span><span class="sxs-lookup"><span data-stu-id="9ce7e-108">Requirements</span></span>  
 <span data-ttu-id="9ce7e-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce7e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce7e-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9ce7e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ce7e-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9ce7e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ce7e-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce7e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce7e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ce7e-113">See also</span></span>

- [<span data-ttu-id="9ce7e-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9ce7e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9ce7e-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9ce7e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
