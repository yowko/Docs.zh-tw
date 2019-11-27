---
title: IMetaDataConverter::GetMetaDataFromTypeLib 方法
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: 6391e819d53c3ed8f0d596b15c4a2bb268f72fd5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436280"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="a7626-102">IMetaDataConverter::GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="a7626-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="a7626-103">取得[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)實例的介面指標，表示指定之 `ITypeLib` 實例所表示之類型程式庫的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="a7626-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7626-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7626-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7626-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7626-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="a7626-106">在代表類型程式庫之 `ITypeLib` 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a7626-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="a7626-107">脫銷位置的指標，接收代表中繼資料簽章之 `IMetaDataImport` 實例的位址。</span><span class="sxs-lookup"><span data-stu-id="a7626-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7626-108">需求</span><span class="sxs-lookup"><span data-stu-id="a7626-108">Requirements</span></span>  
 <span data-ttu-id="a7626-109">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7626-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7626-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a7626-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7626-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a7626-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7626-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7626-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7626-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7626-113">See also</span></span>

- [<span data-ttu-id="a7626-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a7626-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a7626-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a7626-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
