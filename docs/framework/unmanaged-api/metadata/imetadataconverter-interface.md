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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096120"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="7e7df-102">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="7e7df-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="7e7df-103">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="7e7df-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e7df-104">方法</span><span class="sxs-lookup"><span data-stu-id="7e7df-104">Methods</span></span>  
  
|<span data-ttu-id="7e7df-105">方法</span><span class="sxs-lookup"><span data-stu-id="7e7df-105">Method</span></span>|<span data-ttu-id="7e7df-106">描述</span><span class="sxs-lookup"><span data-stu-id="7e7df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e7df-107">GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="7e7df-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="7e7df-108">取得指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)執行個體，表示所指定參考的類型程式庫的中繼資料簽章`ITypeInfo`執行個體。</span><span class="sxs-lookup"><span data-stu-id="7e7df-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="7e7df-109">GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="7e7df-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="7e7df-110">取得指標`IMetaDataImport`執行個體，表示指定所代表的型別程式庫的中繼資料簽章`ITypeLib`執行個體。</span><span class="sxs-lookup"><span data-stu-id="7e7df-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="7e7df-111">GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="7e7df-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="7e7df-112">取得指標`ITypeLib`表示具有指定的模組和程式庫名稱的型別程式庫的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7e7df-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e7df-113">需求</span><span class="sxs-lookup"><span data-stu-id="7e7df-113">Requirements</span></span>  
 <span data-ttu-id="7e7df-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7df-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e7df-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e7df-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e7df-116">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7e7df-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7e7df-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7e7df-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e7df-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7df-118">See also</span></span>

- [<span data-ttu-id="7e7df-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="7e7df-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="7e7df-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7e7df-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
