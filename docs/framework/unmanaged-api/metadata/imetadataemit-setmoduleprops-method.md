---
title: "IMetaDataEmit::SetModuleProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetModuleProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e67acee8092fa20500038bb25e542c3dddb3233e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="ed08a-102">IMetaDataEmit::SetModuleProps 方法</span><span class="sxs-lookup"><span data-stu-id="ed08a-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="ed08a-103">更新在先前呼叫所定義的模組參考[imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ed08a-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed08a-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed08a-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed08a-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed08a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ed08a-106">[in]以 Unicode 模組名稱。</span><span class="sxs-lookup"><span data-stu-id="ed08a-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="ed08a-107">這是檔案名稱而不是完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="ed08a-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed08a-108">需求</span><span class="sxs-lookup"><span data-stu-id="ed08a-108">Requirements</span></span>  
 <span data-ttu-id="ed08a-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed08a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed08a-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ed08a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed08a-111">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ed08a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed08a-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed08a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed08a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed08a-113">See Also</span></span>  
 [<span data-ttu-id="ed08a-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ed08a-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ed08a-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ed08a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
