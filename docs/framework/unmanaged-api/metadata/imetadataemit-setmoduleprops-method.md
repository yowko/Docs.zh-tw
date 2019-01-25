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
ms.openlocfilehash: 86cb99023c0abfc70d292427b14986dbcea1d333
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586159"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="effa3-102">IMetaDataEmit::SetModuleProps 方法</span><span class="sxs-lookup"><span data-stu-id="effa3-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="effa3-103">更新先前呼叫所定義的模組參考[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="effa3-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effa3-104">語法</span><span class="sxs-lookup"><span data-stu-id="effa3-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="effa3-105">參數</span><span class="sxs-lookup"><span data-stu-id="effa3-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="effa3-106">[in]以 Unicode 模組名稱。</span><span class="sxs-lookup"><span data-stu-id="effa3-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="effa3-107">這是檔案名稱而不是完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="effa3-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="effa3-108">需求</span><span class="sxs-lookup"><span data-stu-id="effa3-108">Requirements</span></span>  
 <span data-ttu-id="effa3-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="effa3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="effa3-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="effa3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="effa3-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="effa3-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="effa3-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="effa3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effa3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="effa3-113">See also</span></span>
- [<span data-ttu-id="effa3-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="effa3-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="effa3-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="effa3-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
