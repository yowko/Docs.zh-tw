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
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177638"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="4e9f1-102">IMetaDataConverter::GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="4e9f1-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="4e9f1-103">獲取指向表示具有指定`ITypeLib`庫和模組名稱的型別程式庫的實例的指標。</span><span class="sxs-lookup"><span data-stu-id="4e9f1-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e9f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e9f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e9f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e9f1-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="4e9f1-106">[在]型別程式庫模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e9f1-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="4e9f1-107">[在]型別程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e9f1-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="4e9f1-108">[出]指向接收表示型別程式庫的`ITypeLib`實例位址的位置的指標。</span><span class="sxs-lookup"><span data-stu-id="4e9f1-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e9f1-109">需求</span><span class="sxs-lookup"><span data-stu-id="4e9f1-109">Requirements</span></span>  
 <span data-ttu-id="4e9f1-110">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e9f1-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e9f1-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="4e9f1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e9f1-112">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4e9f1-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e9f1-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e9f1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9f1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e9f1-114">See also</span></span>

- [<span data-ttu-id="4e9f1-115">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="4e9f1-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
