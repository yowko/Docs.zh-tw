---
title: IMetaDataConverter 介面
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d3377617ddd6b82ad88d22f6ffda04b1d6ae837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096120"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="528dc-102">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="528dc-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="528dc-103">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="528dc-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="528dc-104">方法</span><span class="sxs-lookup"><span data-stu-id="528dc-104">Methods</span></span>  
  
|<span data-ttu-id="528dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="528dc-105">Method</span></span>|<span data-ttu-id="528dc-106">描述</span><span class="sxs-lookup"><span data-stu-id="528dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="528dc-107">GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="528dc-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="528dc-108">取得指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)執行個體，表示所指定參考的類型程式庫的中繼資料簽章`ITypeInfo`執行個體。</span><span class="sxs-lookup"><span data-stu-id="528dc-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="528dc-109">GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="528dc-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="528dc-110">取得指標`IMetaDataImport`執行個體，表示指定所代表的型別程式庫的中繼資料簽章`ITypeLib`執行個體。</span><span class="sxs-lookup"><span data-stu-id="528dc-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="528dc-111">GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="528dc-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="528dc-112">取得指標`ITypeLib`表示具有指定的模組和程式庫名稱的型別程式庫的執行個體。</span><span class="sxs-lookup"><span data-stu-id="528dc-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="528dc-113">需求</span><span class="sxs-lookup"><span data-stu-id="528dc-113">Requirements</span></span>  
 <span data-ttu-id="528dc-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="528dc-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="528dc-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="528dc-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="528dc-116">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="528dc-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="528dc-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="528dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528dc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="528dc-118">See also</span></span>

- [<span data-ttu-id="528dc-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="528dc-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="528dc-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="528dc-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
