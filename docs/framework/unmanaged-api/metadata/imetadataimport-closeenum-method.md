---
title: IMetaDataImport::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 724660cd5703ee9b893493df5d583d97b5bdfb3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720518"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="2222d-102">IMetaDataImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="2222d-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="2222d-103">關閉指定的控制代碼所識別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="2222d-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2222d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2222d-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2222d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2222d-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2222d-106">[in]列舉值，以關閉控制代碼。</span><span class="sxs-lookup"><span data-stu-id="2222d-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2222d-107">備註</span><span class="sxs-lookup"><span data-stu-id="2222d-107">Remarks</span></span>  
 <span data-ttu-id="2222d-108">所指定的控制代碼`hEnum`取自於先前`Enum`*名稱*呼叫 (例如[imetadataimport:: Enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md))。</span><span class="sxs-lookup"><span data-stu-id="2222d-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2222d-109">需求</span><span class="sxs-lookup"><span data-stu-id="2222d-109">Requirements</span></span>  
 <span data-ttu-id="2222d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2222d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2222d-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2222d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2222d-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2222d-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2222d-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2222d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2222d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2222d-114">See also</span></span>
- [<span data-ttu-id="2222d-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2222d-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2222d-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2222d-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
