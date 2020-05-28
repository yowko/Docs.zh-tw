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
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008374"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="7a4c2-102">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="7a4c2-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="7a4c2-103">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="7a4c2-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a4c2-104">方法</span><span class="sxs-lookup"><span data-stu-id="7a4c2-104">Methods</span></span>  
  
|<span data-ttu-id="7a4c2-105">方法</span><span class="sxs-lookup"><span data-stu-id="7a4c2-105">Method</span></span>|<span data-ttu-id="7a4c2-106">描述</span><span class="sxs-lookup"><span data-stu-id="7a4c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a4c2-107">GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="7a4c2-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="7a4c2-108">取得[IMetaDataImport](imetadataimport-interface.md)實例的指標，表示指定之實例所參考之類型程式庫的中繼資料簽章 `ITypeInfo` 。</span><span class="sxs-lookup"><span data-stu-id="7a4c2-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="7a4c2-109">GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="7a4c2-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="7a4c2-110">取得 `IMetaDataImport` 實例的指標，表示指定的實例所代表之類型程式庫的中繼資料簽章 `ITypeLib` 。</span><span class="sxs-lookup"><span data-stu-id="7a4c2-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="7a4c2-111">GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="7a4c2-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="7a4c2-112">取得 `ITypeLib` 實例的指標，表示具有指定之模組和程式庫名稱的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="7a4c2-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a4c2-113">需求</span><span class="sxs-lookup"><span data-stu-id="7a4c2-113">Requirements</span></span>  
 <span data-ttu-id="7a4c2-114">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a4c2-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a4c2-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7a4c2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a4c2-116">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7a4c2-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a4c2-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a4c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a4c2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a4c2-118">See also</span></span>

- [<span data-ttu-id="7a4c2-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="7a4c2-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="7a4c2-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7a4c2-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
