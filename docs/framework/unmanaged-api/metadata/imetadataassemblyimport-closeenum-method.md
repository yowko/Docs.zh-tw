---
title: "IMetaDataAssemblyImport::CloseEnum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e015d59ff82c4baa3cefd4a32f393f518f291
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="360a8-102">IMetaDataAssemblyImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="360a8-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="360a8-103">釋放指定之列舉的執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="360a8-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="360a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="360a8-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="360a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="360a8-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="360a8-106">[in]列舉型別執行個體即將關閉。</span><span class="sxs-lookup"><span data-stu-id="360a8-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360a8-107">需求</span><span class="sxs-lookup"><span data-stu-id="360a8-107">Requirements</span></span>  
 <span data-ttu-id="360a8-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="360a8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360a8-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="360a8-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="360a8-110">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="360a8-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="360a8-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="360a8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360a8-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="360a8-112">See Also</span></span>  
 [<span data-ttu-id="360a8-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="360a8-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
