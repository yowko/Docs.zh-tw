---
title: IMetaDataTables2::GetMetaDataStorage 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: 775b3919d1468f26fc3c374dd8ca143aa17853ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708734"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="e10b4-102">IMetaDataTables2::GetMetaDataStorage 方法</span><span class="sxs-lookup"><span data-stu-id="e10b4-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>

<span data-ttu-id="e10b4-103">取得儲存在指定區段中之中繼資料的大小和內容。</span><span class="sxs-lookup"><span data-stu-id="e10b4-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e10b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="e10b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e10b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="e10b4-105">Parameters</span></span>  

 `ppvMd`  
 <span data-ttu-id="e10b4-106">[in，out]中繼資料區段的指標。</span><span class="sxs-lookup"><span data-stu-id="e10b4-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="e10b4-107">擴展中繼資料資料流程的大小。</span><span class="sxs-lookup"><span data-stu-id="e10b4-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e10b4-108">需求</span><span class="sxs-lookup"><span data-stu-id="e10b4-108">Requirements</span></span>  

 <span data-ttu-id="e10b4-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e10b4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e10b4-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e10b4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e10b4-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e10b4-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e10b4-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e10b4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e10b4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e10b4-113">See also</span></span>

- [<span data-ttu-id="e10b4-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="e10b4-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="e10b4-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="e10b4-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
