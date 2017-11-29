---
title: "IMetaDataImport::CloseEnum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 80e156cd92519fc78f2a3076d03b279b7a63c1d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="5de22-102">IMetaDataImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="5de22-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="5de22-103">關閉指定的控制代碼所識別的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5de22-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de22-104">語法</span><span class="sxs-lookup"><span data-stu-id="5de22-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5de22-105">參數</span><span class="sxs-lookup"><span data-stu-id="5de22-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5de22-106">[in]若要關閉的列舉值的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5de22-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5de22-107">備註</span><span class="sxs-lookup"><span data-stu-id="5de22-107">Remarks</span></span>  
 <span data-ttu-id="5de22-108">所指定的控制代碼`hEnum`取自先前`Enum`*名稱*呼叫 (例如， [imetadataimport:: Enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md))。</span><span class="sxs-lookup"><span data-stu-id="5de22-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5de22-109">需求</span><span class="sxs-lookup"><span data-stu-id="5de22-109">Requirements</span></span>  
 <span data-ttu-id="5de22-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5de22-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5de22-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5de22-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5de22-112">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5de22-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5de22-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5de22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5de22-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5de22-114">See Also</span></span>  
 [<span data-ttu-id="5de22-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5de22-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5de22-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5de22-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
