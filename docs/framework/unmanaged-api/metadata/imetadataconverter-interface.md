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
ms.openlocfilehash: 74804cdc9dc04c3ede5cc26a6310dbb3948cd78a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729482"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="4d946-102">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="4d946-102">IMetaDataConverter Interface</span></span>

<span data-ttu-id="4d946-103">提供將類型程式庫對應至它們的中繼資料簽章，以及從一個轉換到另一個的方法。</span><span class="sxs-lookup"><span data-stu-id="4d946-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d946-104">方法</span><span class="sxs-lookup"><span data-stu-id="4d946-104">Methods</span></span>  
  
|<span data-ttu-id="4d946-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d946-105">Method</span></span>|<span data-ttu-id="4d946-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d946-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d946-107">GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="4d946-107">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="4d946-108">取得 [IMetaDataImport](imetadataimport-interface.md) 實例的指標，該實例表示指定實例所參考之類型程式庫的中繼資料簽章 `ITypeInfo` 。</span><span class="sxs-lookup"><span data-stu-id="4d946-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="4d946-109">GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="4d946-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="4d946-110">取得 `IMetaDataImport` 實例的指標，該實例表示指定實例所代表之類型程式庫的中繼資料簽章 `ITypeLib` 。</span><span class="sxs-lookup"><span data-stu-id="4d946-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="4d946-111">GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="4d946-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="4d946-112">取得 `ITypeLib` 實例的指標，該實例表示具有指定模組和程式庫名稱的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="4d946-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d946-113">需求</span><span class="sxs-lookup"><span data-stu-id="4d946-113">Requirements</span></span>  

 <span data-ttu-id="4d946-114">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d946-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d946-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4d946-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d946-116">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4d946-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d946-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d946-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d946-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d946-118">See also</span></span>

- [<span data-ttu-id="4d946-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="4d946-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="4d946-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4d946-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
