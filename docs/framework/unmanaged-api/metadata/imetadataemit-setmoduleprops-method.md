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
ms.openlocfilehash: ce8be38f6e146b2a8669ea5c694353615f6f2d66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445899"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="1799f-102">IMetaDataEmit::SetModuleProps 方法</span><span class="sxs-lookup"><span data-stu-id="1799f-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="1799f-103">更新在先前呼叫所定義的模組參考[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="1799f-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1799f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1799f-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1799f-105">參數</span><span class="sxs-lookup"><span data-stu-id="1799f-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1799f-106">[in]以 Unicode 模組名稱。</span><span class="sxs-lookup"><span data-stu-id="1799f-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="1799f-107">這是檔案名稱而不是完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="1799f-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1799f-108">需求</span><span class="sxs-lookup"><span data-stu-id="1799f-108">Requirements</span></span>  
 <span data-ttu-id="1799f-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1799f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1799f-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1799f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1799f-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1799f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1799f-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1799f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1799f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1799f-113">See Also</span></span>  
 [<span data-ttu-id="1799f-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1799f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1799f-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1799f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
