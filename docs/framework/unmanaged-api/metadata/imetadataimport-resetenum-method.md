---
title: IMetaDataImport::ResetEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 3dd82588cf2dbf92fdda66fd7674c17ddc8b7306
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177195"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="e5571-102">IMetaDataImport::ResetEnum 方法</span><span class="sxs-lookup"><span data-stu-id="e5571-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="e5571-103">重設指定列舉程式至指定位置。</span><span class="sxs-lookup"><span data-stu-id="e5571-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5571-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5571-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5571-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5571-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e5571-106">[在]要重置的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="e5571-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="e5571-107">[在]放置枚舉器的新位置。</span><span class="sxs-lookup"><span data-stu-id="e5571-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5571-108">需求</span><span class="sxs-lookup"><span data-stu-id="e5571-108">Requirements</span></span>  
 <span data-ttu-id="e5571-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5571-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5571-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="e5571-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5571-111">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e5571-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5571-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5571-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5571-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5571-113">See also</span></span>

- [<span data-ttu-id="e5571-114">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e5571-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e5571-115">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e5571-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
