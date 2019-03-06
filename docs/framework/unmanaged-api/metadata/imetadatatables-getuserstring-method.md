---
title: IMetaDataTables::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fefbab6b2ea9fbbfd90e03c41578a924f99c7a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364160"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="9e09f-102">IMetaDataTables::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="9e09f-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="9e09f-103">取得在目前範圍中的字串資料行中的指定索引處的硬式編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="9e09f-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e09f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e09f-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="9e09f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e09f-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="9e09f-106">[in]硬式編碼的字串將擷取的索引值。</span><span class="sxs-lookup"><span data-stu-id="9e09f-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="9e09f-107">[out]大小的指標`ppData`。</span><span class="sxs-lookup"><span data-stu-id="9e09f-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="9e09f-108">[out]傳回的字串指標的指標。</span><span class="sxs-lookup"><span data-stu-id="9e09f-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e09f-109">需求</span><span class="sxs-lookup"><span data-stu-id="9e09f-109">Requirements</span></span>

<span data-ttu-id="9e09f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e09f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9e09f-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9e09f-111">**Header:** Cor.h</span></span>

<span data-ttu-id="9e09f-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e09f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="9e09f-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e09f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9e09f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e09f-114">See also</span></span>

- [<span data-ttu-id="9e09f-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="9e09f-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9e09f-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="9e09f-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)