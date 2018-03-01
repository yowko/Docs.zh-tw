---
title: "IMetaDataConverter::GetMetaDataFromTypeInfo 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66e090efc9ce8a8fc1ca5de8d8f7a60f9ca17b9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="4d04b-102">IMetaDataConverter::GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="4d04b-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="4d04b-103">取得指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)執行個體，表示指定所參考的類型程式庫的中繼資料簽章`ITypeInfo`執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d04b-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d04b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d04b-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d04b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d04b-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="4d04b-106">[in]指標`ITypeInfo`指的是型別程式庫的物件。</span><span class="sxs-lookup"><span data-stu-id="4d04b-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="4d04b-107">[out]接收的位址的位置的指標`IMetaDataImport`代表中繼資料簽章的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d04b-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d04b-108">需求</span><span class="sxs-lookup"><span data-stu-id="4d04b-108">Requirements</span></span>  
 <span data-ttu-id="4d04b-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d04b-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d04b-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d04b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d04b-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4d04b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d04b-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d04b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d04b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d04b-113">See Also</span></span>  
 [<span data-ttu-id="4d04b-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4d04b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4d04b-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4d04b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
