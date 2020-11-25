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
ms.openlocfilehash: 21fc79f62dba4b16a7a067dff8fb9dcc795c9d35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708721"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="43ace-102">IMetaDataTables2::GetMetaDataStreamInfo 方法</span><span class="sxs-lookup"><span data-stu-id="43ace-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>

<span data-ttu-id="43ace-103">取得位於指定索引處之中繼資料資料流程的名稱、大小和內容。</span><span class="sxs-lookup"><span data-stu-id="43ace-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ace-104">語法</span><span class="sxs-lookup"><span data-stu-id="43ace-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ace-105">參數</span><span class="sxs-lookup"><span data-stu-id="43ace-105">Parameters</span></span>  

 `ix`  
 <span data-ttu-id="43ace-106">在要求的中繼資料資料流程的索引。</span><span class="sxs-lookup"><span data-stu-id="43ace-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="43ace-107">擴展資料流程名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="43ace-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="43ace-108">擴展中繼資料資料流程的指標。</span><span class="sxs-lookup"><span data-stu-id="43ace-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="43ace-109">擴展的大小（以位元組為單位） `ppv` 。</span><span class="sxs-lookup"><span data-stu-id="43ace-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ace-110">需求</span><span class="sxs-lookup"><span data-stu-id="43ace-110">Requirements</span></span>  

 <span data-ttu-id="43ace-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43ace-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ace-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="43ace-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43ace-113">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="43ace-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43ace-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ace-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ace-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43ace-115">See also</span></span>

- [<span data-ttu-id="43ace-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="43ace-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="43ace-117">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="43ace-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
