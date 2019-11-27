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
ms.openlocfilehash: 279e34689169d31ad89772e90155e7f50bdbac08
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426224"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="044a1-102">IMetaDataTables2::GetMetaDataStreamInfo 方法</span><span class="sxs-lookup"><span data-stu-id="044a1-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="044a1-103">取得指定索引處中繼資料資料流程的名稱、大小和內容。</span><span class="sxs-lookup"><span data-stu-id="044a1-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="044a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="044a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="044a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="044a1-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="044a1-106">在要求之中繼資料資料流程的索引。</span><span class="sxs-lookup"><span data-stu-id="044a1-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="044a1-107">脫銷資料流程名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="044a1-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="044a1-108">脫銷中繼資料資料流程的指標。</span><span class="sxs-lookup"><span data-stu-id="044a1-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="044a1-109">脫銷`ppv`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="044a1-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="044a1-110">需求</span><span class="sxs-lookup"><span data-stu-id="044a1-110">Requirements</span></span>  
 <span data-ttu-id="044a1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="044a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="044a1-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="044a1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="044a1-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="044a1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="044a1-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="044a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044a1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="044a1-115">See also</span></span>

- [<span data-ttu-id="044a1-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="044a1-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="044a1-117">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="044a1-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
