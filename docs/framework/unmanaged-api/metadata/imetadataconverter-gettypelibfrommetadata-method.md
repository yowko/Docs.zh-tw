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
ms.openlocfilehash: 9da4e34fa948db2fc73cbde813bac9b3430605ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436257"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="38039-102">IMetaDataConverter::GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="38039-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="38039-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span><span class="sxs-lookup"><span data-stu-id="38039-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38039-104">語法</span><span class="sxs-lookup"><span data-stu-id="38039-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38039-105">參數</span><span class="sxs-lookup"><span data-stu-id="38039-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="38039-106">[in] The name of the type library's module.</span><span class="sxs-lookup"><span data-stu-id="38039-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="38039-107">[in] The name of the type library.</span><span class="sxs-lookup"><span data-stu-id="38039-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="38039-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span><span class="sxs-lookup"><span data-stu-id="38039-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38039-109">需求</span><span class="sxs-lookup"><span data-stu-id="38039-109">Requirements</span></span>  
 <span data-ttu-id="38039-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38039-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38039-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38039-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38039-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38039-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38039-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38039-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38039-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="38039-114">See also</span></span>

- [<span data-ttu-id="38039-115">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="38039-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
