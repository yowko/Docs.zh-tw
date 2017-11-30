---
title: "IMetaDataImport::CountEnum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.CountEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29bbc78da38ca65b2c19c5f0d93a273ba3ac0da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="64d8a-102">IMetaDataImport::CountEnum 方法</span><span class="sxs-lookup"><span data-stu-id="64d8a-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="64d8a-103">擷取所指定的列舉值的列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="64d8a-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="64d8a-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64d8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="64d8a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="64d8a-106">[in]列舉值控制代碼。</span><span class="sxs-lookup"><span data-stu-id="64d8a-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="64d8a-107">[out]列舉的元素數目。</span><span class="sxs-lookup"><span data-stu-id="64d8a-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64d8a-108">備註</span><span class="sxs-lookup"><span data-stu-id="64d8a-108">Remarks</span></span>  
 <span data-ttu-id="64d8a-109">所指定的控制代碼`hEnum`取自先前`Enum`*名稱*呼叫 (例如， [imetadataimport:: Enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md))。</span><span class="sxs-lookup"><span data-stu-id="64d8a-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d8a-110">需求</span><span class="sxs-lookup"><span data-stu-id="64d8a-110">Requirements</span></span>  
 <span data-ttu-id="64d8a-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64d8a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d8a-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="64d8a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64d8a-113">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="64d8a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64d8a-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d8a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d8a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64d8a-115">See Also</span></span>  
 [<span data-ttu-id="64d8a-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="64d8a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="64d8a-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="64d8a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
