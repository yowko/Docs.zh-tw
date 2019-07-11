---
title: IMetaDataTables::GetNumTables 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb26a96c46b01a2981afba0ac6b405c0b50f6d9a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781426"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="607b5-102">IMetaDataTables::GetNumTables 方法</span><span class="sxs-lookup"><span data-stu-id="607b5-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="607b5-103">取得目前的範圍中的資料表數目`IMetaDataTables`執行個體。</span><span class="sxs-lookup"><span data-stu-id="607b5-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="607b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="607b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="607b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="607b5-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="607b5-106">[out]目前的執行個體範圍中的資料表數目指標。</span><span class="sxs-lookup"><span data-stu-id="607b5-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="607b5-107">需求</span><span class="sxs-lookup"><span data-stu-id="607b5-107">Requirements</span></span>  
 <span data-ttu-id="607b5-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="607b5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="607b5-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="607b5-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="607b5-110">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="607b5-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="607b5-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="607b5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607b5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="607b5-112">See also</span></span>

- [<span data-ttu-id="607b5-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="607b5-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="607b5-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="607b5-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
