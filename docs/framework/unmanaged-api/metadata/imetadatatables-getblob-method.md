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
ms.openlocfilehash: f5a736d80f36afb8d0a643d4a4e36c9abff01995
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445436"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="d2a18-102">IMetaDataTables::GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="d2a18-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="d2a18-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span><span class="sxs-lookup"><span data-stu-id="d2a18-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a18-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2a18-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2a18-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2a18-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="d2a18-106">[in] The memory address from which to get `ppData`.</span><span class="sxs-lookup"><span data-stu-id="d2a18-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="d2a18-107">[out] A pointer to the size, in bytes, of `ppData`.</span><span class="sxs-lookup"><span data-stu-id="d2a18-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="d2a18-108">[out] A pointer to a pointer to the binary data retrieved.</span><span class="sxs-lookup"><span data-stu-id="d2a18-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a18-109">需求</span><span class="sxs-lookup"><span data-stu-id="d2a18-109">Requirements</span></span>  
 <span data-ttu-id="d2a18-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a18-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a18-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2a18-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2a18-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2a18-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2a18-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a18-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a18-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d2a18-114">See also</span></span>

- [<span data-ttu-id="d2a18-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="d2a18-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d2a18-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="d2a18-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
