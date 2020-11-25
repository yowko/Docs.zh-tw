---
title: IMetaDataTables::GetBlob 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: 32f32625ee40d50249ce3e009add543c4137b196
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726466"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="9ab92-102">IMetaDataTables::GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="9ab92-102">IMetaDataTables::GetBlob Method</span></span>

<span data-ttu-id="9ab92-103">取得在指定的資料行索引上 (BLOB) 之二進位大型物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9ab92-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab92-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ab92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ab92-105">參數</span><span class="sxs-lookup"><span data-stu-id="9ab92-105">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="9ab92-106">在要從中取得的記憶體位址 `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="9ab92-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="9ab92-107">擴展大小的指標，以位元組為單位 `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="9ab92-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="9ab92-108">擴展已抓取之二進位資料指標的指標。</span><span class="sxs-lookup"><span data-stu-id="9ab92-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab92-109">需求</span><span class="sxs-lookup"><span data-stu-id="9ab92-109">Requirements</span></span>  

 <span data-ttu-id="9ab92-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab92-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab92-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9ab92-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ab92-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="9ab92-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ab92-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab92-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab92-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab92-114">See also</span></span>

- [<span data-ttu-id="9ab92-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="9ab92-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9ab92-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="9ab92-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
