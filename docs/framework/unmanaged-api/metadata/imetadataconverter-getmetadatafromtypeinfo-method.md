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
ms.openlocfilehash: 1f45310bc65bc8614033182a81db451b79bcf97f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714714"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="a9dc8-102">IMetaDataConverter::GetMetaDataFromTypeInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a9dc8-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>

<span data-ttu-id="a9dc8-103">取得 [IMetaDataImport](imetadataimport-interface.md) 實例的指標，該實例表示指定實例所參考之類型程式庫的中繼資料簽章 `ITypeInfo` 。</span><span class="sxs-lookup"><span data-stu-id="a9dc8-103">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9dc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9dc8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9dc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9dc8-105">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="a9dc8-106">在 `ITypeInfo` 參考類型程式庫之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a9dc8-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="a9dc8-107">擴展位置的指標，此位置會接收表示中繼資料簽章之實例的位址 `IMetaDataImport` 。</span><span class="sxs-lookup"><span data-stu-id="a9dc8-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9dc8-108">需求</span><span class="sxs-lookup"><span data-stu-id="a9dc8-108">Requirements</span></span>  

 <span data-ttu-id="a9dc8-109">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9dc8-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9dc8-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a9dc8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9dc8-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a9dc8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9dc8-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9dc8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9dc8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9dc8-113">See also</span></span>

- [<span data-ttu-id="a9dc8-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a9dc8-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a9dc8-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a9dc8-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
