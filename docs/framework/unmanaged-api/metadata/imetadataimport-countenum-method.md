---
title: IMetaDataImport::CountEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: 0c78ce8192d6456dd1b1be990d87b9209b028e09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440365"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="32487-102">IMetaDataImport::CountEnum 方法</span><span class="sxs-lookup"><span data-stu-id="32487-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="32487-103">取得列舉中指定的列舉值所抓取的元素數目。</span><span class="sxs-lookup"><span data-stu-id="32487-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32487-104">語法</span><span class="sxs-lookup"><span data-stu-id="32487-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32487-105">參數</span><span class="sxs-lookup"><span data-stu-id="32487-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="32487-106">在列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="32487-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="32487-107">脫銷列舉的元素數目。</span><span class="sxs-lookup"><span data-stu-id="32487-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32487-108">備註</span><span class="sxs-lookup"><span data-stu-id="32487-108">Remarks</span></span>  
 <span data-ttu-id="32487-109">`hEnum` 所指定的控制碼是從先前的 `Enum`*名稱*呼叫取得（例如， [IMetaDataImport：： EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)）。</span><span class="sxs-lookup"><span data-stu-id="32487-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32487-110">需求</span><span class="sxs-lookup"><span data-stu-id="32487-110">Requirements</span></span>  
 <span data-ttu-id="32487-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32487-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32487-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="32487-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32487-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="32487-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32487-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32487-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32487-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32487-115">See also</span></span>

- [<span data-ttu-id="32487-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="32487-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="32487-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="32487-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
