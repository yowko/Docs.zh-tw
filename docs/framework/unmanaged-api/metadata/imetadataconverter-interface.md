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
# <a name="imetadataconverter-interface"></a><span data-ttu-id="c62c8-102">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="c62c8-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="c62c8-103">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="c62c8-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c62c8-104">方法</span><span class="sxs-lookup"><span data-stu-id="c62c8-104">Methods</span></span>  
  
|<span data-ttu-id="c62c8-105">方法</span><span class="sxs-lookup"><span data-stu-id="c62c8-105">Method</span></span>|<span data-ttu-id="c62c8-106">描述</span><span class="sxs-lookup"><span data-stu-id="c62c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c62c8-107">GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="c62c8-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="c62c8-108">取得[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)實例的指標，表示指定之 `ITypeInfo` 實例所參考之類型程式庫的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="c62c8-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="c62c8-109">GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="c62c8-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="c62c8-110">取得 `IMetaDataImport` 實例的指標，表示指定 `ITypeLib` 實例所表示之類型程式庫的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="c62c8-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="c62c8-111">GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="c62c8-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="c62c8-112">取得 `ITypeLib` 實例的指標，表示具有指定之模組和程式庫名稱的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="c62c8-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c62c8-113">需求</span><span class="sxs-lookup"><span data-stu-id="c62c8-113">Requirements</span></span>  
 <span data-ttu-id="c62c8-114">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c62c8-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c62c8-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c62c8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c62c8-116">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c62c8-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c62c8-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c62c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62c8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c62c8-118">See also</span></span>

- [<span data-ttu-id="c62c8-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="c62c8-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="c62c8-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c62c8-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
