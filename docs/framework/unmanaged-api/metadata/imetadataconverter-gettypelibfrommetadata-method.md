---
title: IMetaDataConverter::GetTypeLibFromMetaData 方法
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ab1d39ddb53e08e6fd36016f544162e2b11edb0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472066"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="933a2-102">IMetaDataConverter::GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="933a2-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="933a2-103">取得指標`ITypeLib`表示具有指定的程式庫和模組名稱的型別程式庫的執行個體。</span><span class="sxs-lookup"><span data-stu-id="933a2-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="933a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="933a2-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="933a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="933a2-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="933a2-106">[in]型別程式庫的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="933a2-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="933a2-107">[in]型別程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="933a2-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="933a2-108">[out]接收的地址的位置指標`ITypeLib`執行個體，表示型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="933a2-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="933a2-109">需求</span><span class="sxs-lookup"><span data-stu-id="933a2-109">Requirements</span></span>  
 <span data-ttu-id="933a2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="933a2-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933a2-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="933a2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="933a2-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="933a2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="933a2-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933a2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933a2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="933a2-114">See also</span></span>
- [<span data-ttu-id="933a2-115">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="933a2-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
