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
ms.openlocfilehash: 651659a48ba9950cdd837889c4491c66fe40b507
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042965"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="39dc0-102">IMetaDataEmit::SetModuleProps 方法</span><span class="sxs-lookup"><span data-stu-id="39dc0-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="39dc0-103">更新先前呼叫所定義的模組參考[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="39dc0-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39dc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="39dc0-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39dc0-105">參數</span><span class="sxs-lookup"><span data-stu-id="39dc0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="39dc0-106">[in]以 Unicode 模組名稱。</span><span class="sxs-lookup"><span data-stu-id="39dc0-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="39dc0-107">這是檔案名稱而不是完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="39dc0-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39dc0-108">需求</span><span class="sxs-lookup"><span data-stu-id="39dc0-108">Requirements</span></span>  
 <span data-ttu-id="39dc0-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39dc0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39dc0-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="39dc0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39dc0-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="39dc0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39dc0-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39dc0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39dc0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39dc0-113">See also</span></span>

- [<span data-ttu-id="39dc0-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="39dc0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="39dc0-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="39dc0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
