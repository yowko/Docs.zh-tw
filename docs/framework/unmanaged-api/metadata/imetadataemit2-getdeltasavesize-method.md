---
title: IMetaDataEmit2::GetDeltaSaveSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 36021333c1efb61e23c16782d8ad721de62c2643
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674311"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="0b8fc-102">IMetaDataEmit2::GetDeltaSaveSize 方法</span><span class="sxs-lookup"><span data-stu-id="0b8fc-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>

<span data-ttu-id="0b8fc-103">取得值，指出目前的編輯後繼續會話所產生之中繼資料大小的任何變更。</span><span class="sxs-lookup"><span data-stu-id="0b8fc-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b8fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b8fc-105">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="0b8fc-106">在其中一個 [CorSaveSize](corsavesize-enumeration.md) 值，表示所需的有效位數層級。</span><span class="sxs-lookup"><span data-stu-id="0b8fc-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="0b8fc-107">針對 .NET Framework 版本2.0，會忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="0b8fc-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="0b8fc-108">擴展中繼資料大小的變更。</span><span class="sxs-lookup"><span data-stu-id="0b8fc-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b8fc-109">需求</span><span class="sxs-lookup"><span data-stu-id="0b8fc-109">Requirements</span></span>  

 <span data-ttu-id="0b8fc-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b8fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b8fc-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="0b8fc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b8fc-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="0b8fc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b8fc-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b8fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8fc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b8fc-114">See also</span></span>

- [<span data-ttu-id="0b8fc-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="0b8fc-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="0b8fc-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0b8fc-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
