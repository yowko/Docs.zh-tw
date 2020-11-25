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
ms.openlocfilehash: ed0902824bdbb4d057bf5a7920db4b1d18eb7347
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714662"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="03e49-102">IMetaDataConverter::GetMetaDataFromTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="03e49-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>

<span data-ttu-id="03e49-103">取得 [IMetaDataImport](imetadataimport-interface.md) 實例的介面指標，表示指定實例所代表之類型程式庫的中繼資料簽章 `ITypeLib` 。</span><span class="sxs-lookup"><span data-stu-id="03e49-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e49-104">語法</span><span class="sxs-lookup"><span data-stu-id="03e49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03e49-105">參數</span><span class="sxs-lookup"><span data-stu-id="03e49-105">Parameters</span></span>  

 `pITL`  
 <span data-ttu-id="03e49-106">在 `ITypeLib` 代表類型程式庫之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="03e49-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="03e49-107">擴展位置的指標，此位置會接收表示中繼資料簽章之實例的位址 `IMetaDataImport` 。</span><span class="sxs-lookup"><span data-stu-id="03e49-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e49-108">需求</span><span class="sxs-lookup"><span data-stu-id="03e49-108">Requirements</span></span>  

 <span data-ttu-id="03e49-109">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03e49-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e49-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="03e49-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03e49-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="03e49-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03e49-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e49-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e49-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03e49-113">See also</span></span>

- [<span data-ttu-id="03e49-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="03e49-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="03e49-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="03e49-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
