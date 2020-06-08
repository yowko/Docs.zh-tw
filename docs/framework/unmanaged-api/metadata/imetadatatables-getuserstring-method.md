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
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501140"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="1f21b-102">IMetaDataTables::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="1f21b-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="1f21b-103">取得在目前範圍的字串資料行中指定索引處的硬式編碼字串。</span><span class="sxs-lookup"><span data-stu-id="1f21b-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f21b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f21b-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="1f21b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f21b-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="1f21b-106">在將從中抓取硬式編碼字串的索引值。</span><span class="sxs-lookup"><span data-stu-id="1f21b-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="1f21b-107">脫銷大小的指標 `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="1f21b-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="1f21b-108">脫銷傳回之字串指標的指標。</span><span class="sxs-lookup"><span data-stu-id="1f21b-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f21b-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="1f21b-109">Requirements</span></span>

<span data-ttu-id="1f21b-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f21b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1f21b-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1f21b-111">**Header:** Cor.h</span></span>

<span data-ttu-id="1f21b-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1f21b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="1f21b-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f21b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1f21b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f21b-114">See also</span></span>

- [<span data-ttu-id="1f21b-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="1f21b-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1f21b-116">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="1f21b-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
