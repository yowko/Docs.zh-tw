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
ms.openlocfilehash: 79bd8901641ee587e94861c0aec85b812591ea48
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008413"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="7a43a-102">IMetaDataConverter::GetTypeLibFromMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="7a43a-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="7a43a-103">取得 `ITypeLib` 實例的指標，表示具有指定之程式庫和模組名稱的類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="7a43a-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a43a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a43a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a43a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a43a-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="7a43a-106">在型別程式庫模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a43a-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="7a43a-107">在類型程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a43a-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="7a43a-108">脫銷位置的指標，接收 `ITypeLib` 代表類型程式庫之實例的位址。</span><span class="sxs-lookup"><span data-stu-id="7a43a-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a43a-109">需求</span><span class="sxs-lookup"><span data-stu-id="7a43a-109">Requirements</span></span>  
 <span data-ttu-id="7a43a-110">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a43a-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a43a-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7a43a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a43a-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7a43a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a43a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a43a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a43a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a43a-114">See also</span></span>

- [<span data-ttu-id="7a43a-115">IMetaDataConverter 介面</span><span class="sxs-lookup"><span data-stu-id="7a43a-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
