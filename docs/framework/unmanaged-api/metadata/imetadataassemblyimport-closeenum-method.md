---
title: IMetaDataAssemblyImport::CloseEnum 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 156b2274aa442d9efb129d51ccf5939a09ac7408
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710127"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="5d905-102">IMetaDataAssemblyImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="5d905-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="5d905-103">釋放指定的列舉型別執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="5d905-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d905-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d905-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d905-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d905-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5d905-106">[in]若要關閉列舉型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d905-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d905-107">需求</span><span class="sxs-lookup"><span data-stu-id="5d905-107">Requirements</span></span>  
 <span data-ttu-id="5d905-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d905-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d905-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5d905-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d905-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5d905-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d905-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d905-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d905-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d905-112">See also</span></span>
- [<span data-ttu-id="5d905-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="5d905-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
