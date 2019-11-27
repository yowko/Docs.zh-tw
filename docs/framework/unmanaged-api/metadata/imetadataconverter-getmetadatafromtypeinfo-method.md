---
title: IMetaDataConverter::GetMetaDataFromTypeInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: df7be11e8f275824fca658a9604178e7cf28e3ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436299"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="59cf5-102">IMetaDataConverter::GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="59cf5-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="59cf5-103">取得[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)實例的指標，表示指定之 `ITypeInfo` 實例所參考之類型程式庫的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="59cf5-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59cf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="59cf5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59cf5-105">參數</span><span class="sxs-lookup"><span data-stu-id="59cf5-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="59cf5-106">在參考型別程式庫之 `ITypeInfo` 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="59cf5-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="59cf5-107">脫銷位置的指標，接收代表中繼資料簽章之 `IMetaDataImport` 實例的位址。</span><span class="sxs-lookup"><span data-stu-id="59cf5-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cf5-108">需求</span><span class="sxs-lookup"><span data-stu-id="59cf5-108">Requirements</span></span>  
 <span data-ttu-id="59cf5-109">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59cf5-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59cf5-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="59cf5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59cf5-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="59cf5-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59cf5-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cf5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cf5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59cf5-113">See also</span></span>

- [<span data-ttu-id="59cf5-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="59cf5-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="59cf5-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="59cf5-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
