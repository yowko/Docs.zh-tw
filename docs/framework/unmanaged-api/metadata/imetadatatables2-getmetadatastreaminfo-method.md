---
title: IMetaDataTables2::GetMetaDataStreamInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 7d39d089c348b7320651ed21ea14ba07d7877fd4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501091"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="57f52-102">IMetaDataTables2::GetMetaDataStreamInfo 方法</span><span class="sxs-lookup"><span data-stu-id="57f52-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="57f52-103">取得指定索引處中繼資料資料流程的名稱、大小和內容。</span><span class="sxs-lookup"><span data-stu-id="57f52-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f52-104">語法</span><span class="sxs-lookup"><span data-stu-id="57f52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57f52-105">參數</span><span class="sxs-lookup"><span data-stu-id="57f52-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="57f52-106">在要求之中繼資料資料流程的索引。</span><span class="sxs-lookup"><span data-stu-id="57f52-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="57f52-107">脫銷資料流程名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="57f52-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="57f52-108">脫銷中繼資料資料流程的指標。</span><span class="sxs-lookup"><span data-stu-id="57f52-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="57f52-109">脫銷的大小（以位元組為單位） `ppv` 。</span><span class="sxs-lookup"><span data-stu-id="57f52-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57f52-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="57f52-110">Requirements</span></span>  
 <span data-ttu-id="57f52-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57f52-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f52-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="57f52-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57f52-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="57f52-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57f52-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57f52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f52-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57f52-115">See also</span></span>

- [<span data-ttu-id="57f52-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="57f52-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="57f52-117">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="57f52-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
