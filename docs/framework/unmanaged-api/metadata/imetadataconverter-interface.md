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
ms.openlocfilehash: b771b368c069a4577d266b47bfb4a5ee1935e48e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436265"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="367ce-102">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="367ce-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="367ce-103">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="367ce-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="367ce-104">方法</span><span class="sxs-lookup"><span data-stu-id="367ce-104">Methods</span></span>  
  
|<span data-ttu-id="367ce-105">方法</span><span class="sxs-lookup"><span data-stu-id="367ce-105">Method</span></span>|<span data-ttu-id="367ce-106">描述</span><span class="sxs-lookup"><span data-stu-id="367ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="367ce-107">GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="367ce-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="367ce-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="367ce-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="367ce-109">GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="367ce-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="367ce-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="367ce-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="367ce-111">GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="367ce-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="367ce-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span><span class="sxs-lookup"><span data-stu-id="367ce-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="367ce-113">需求</span><span class="sxs-lookup"><span data-stu-id="367ce-113">Requirements</span></span>  
 <span data-ttu-id="367ce-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="367ce-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="367ce-115">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="367ce-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="367ce-116">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="367ce-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="367ce-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="367ce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367ce-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="367ce-118">See also</span></span>

- [<span data-ttu-id="367ce-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="367ce-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="367ce-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="367ce-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
