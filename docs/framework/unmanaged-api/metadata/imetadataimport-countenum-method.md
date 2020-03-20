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
ms.openlocfilehash: b780ca513d8a0b4f88e66594e86e9ff8290f6523
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177352"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="3eedb-102">IMetaDataImport::CountEnum 方法</span><span class="sxs-lookup"><span data-stu-id="3eedb-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="3eedb-103">獲取指定枚舉器檢索的枚舉中的元素數。</span><span class="sxs-lookup"><span data-stu-id="3eedb-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eedb-104">語法</span><span class="sxs-lookup"><span data-stu-id="3eedb-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eedb-105">參數</span><span class="sxs-lookup"><span data-stu-id="3eedb-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3eedb-106">[在]枚舉器的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3eedb-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="3eedb-107">[出]枚舉的元素數。</span><span class="sxs-lookup"><span data-stu-id="3eedb-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eedb-108">備註</span><span class="sxs-lookup"><span data-stu-id="3eedb-108">Remarks</span></span>  
 <span data-ttu-id="3eedb-109">指定的`hEnum`控制碼是從以前的`Enum` *Name*調用（例如[，IMetaDataImport：：enumTypeDefs）獲取的](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3eedb-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eedb-110">需求</span><span class="sxs-lookup"><span data-stu-id="3eedb-110">Requirements</span></span>  
 <span data-ttu-id="3eedb-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3eedb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eedb-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="3eedb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3eedb-113">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3eedb-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3eedb-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eedb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eedb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eedb-115">See also</span></span>

- [<span data-ttu-id="3eedb-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3eedb-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3eedb-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3eedb-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
