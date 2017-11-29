---
title: "IMetaDataConverter::GetMetaDataFromTypeLib 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter.GetMetaDataFromTypeLib
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f2438c2d5402f6cff695ecc9832329ff826ded01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="58613-102">IMetaDataConverter::GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="58613-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="58613-103">取得的介面指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)執行個體，表示由指定的類型程式庫的中繼資料簽章`ITypeLib`執行個體。</span><span class="sxs-lookup"><span data-stu-id="58613-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58613-104">語法</span><span class="sxs-lookup"><span data-stu-id="58613-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58613-105">參數</span><span class="sxs-lookup"><span data-stu-id="58613-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="58613-106">[in]指標`ITypeLib`物件，表示型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="58613-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="58613-107">[out]接收的位址的位置指標`IMetaDataImport`代表中繼資料簽章的執行個體。</span><span class="sxs-lookup"><span data-stu-id="58613-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58613-108">需求</span><span class="sxs-lookup"><span data-stu-id="58613-108">Requirements</span></span>  
 <span data-ttu-id="58613-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58613-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58613-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58613-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58613-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="58613-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58613-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58613-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58613-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58613-113">See Also</span></span>  
 [<span data-ttu-id="58613-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="58613-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="58613-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="58613-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
