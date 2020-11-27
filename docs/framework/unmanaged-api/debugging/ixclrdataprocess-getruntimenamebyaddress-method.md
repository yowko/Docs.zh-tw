---
title: IXCLRDataProcess：： GetRuntimeNameByAddress 方法
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270481"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a><span data-ttu-id="3e714-102">IXCLRDataProcess：： GetRuntimeNameByAddress 方法</span><span class="sxs-lookup"><span data-stu-id="3e714-102">IXCLRDataProcess::GetRuntimeNameByAddress Method</span></span>

<span data-ttu-id="3e714-103">取得指定位址的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e714-103">Gets a name for the given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="3e714-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e714-104">Syntax</span></span>

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a><span data-ttu-id="3e714-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e714-105">Parameters</span></span>

`address`\
<span data-ttu-id="3e714-106">在 `CLRDATA_ADDRESS` 表示程式碼位址的值。</span><span class="sxs-lookup"><span data-stu-id="3e714-106">[in] A `CLRDATA_ADDRESS` value that represents a code address.</span></span>

`flags`\
<span data-ttu-id="3e714-107">在設定為 ' 0 '。</span><span class="sxs-lookup"><span data-stu-id="3e714-107">[in] Set to '0'.</span></span>

`bufLen`\
<span data-ttu-id="3e714-108">在緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="3e714-108">[in] The length of the buffer.</span></span>

`namLen`\
<span data-ttu-id="3e714-109">擴展傳回的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="3e714-109">[out] A pointer to the number of characters returned.</span></span>

`namBuf`\
<span data-ttu-id="3e714-110">[out，size_is (`bufLen`) ] 儲存執行時間名稱之長度的輸入緩衝區 `bufLen` 。</span><span class="sxs-lookup"><span data-stu-id="3e714-110">[out, size_is(`bufLen`)] The input buffer of length `bufLen` that stores the runtime name.</span></span>

`displacement`\
<span data-ttu-id="3e714-111">擴展 `CLRDATA_ADDRESS` 傳回之符號的程式碼位移指標。</span><span class="sxs-lookup"><span data-stu-id="3e714-111">[out] A `CLRDATA_ADDRESS` pointer to the code offset of the returned symbol.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e714-112">備註</span><span class="sxs-lookup"><span data-stu-id="3e714-112">Remarks</span></span>

<span data-ttu-id="3e714-113">提供的方法是介面的一部分 `IXCLRDataProcess` ，而且會對應至虛擬方法資料表的第16個位置。</span><span class="sxs-lookup"><span data-stu-id="3e714-113">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 16th slot of the virtual-method table.</span></span>

> [!NOTE]
> <span data-ttu-id="3e714-114">如果緩衝區不夠大，無法用於名稱，這個方法會傳回 `S_FALSE` 並設定 `nameLen` 為所需的緩衝區長度。</span><span class="sxs-lookup"><span data-stu-id="3e714-114">If the buffer is not large enough for the name, this method returns `S_FALSE` and sets `nameLen` to the required buffer length.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e714-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="3e714-115">Requirements</span></span>

<span data-ttu-id="3e714-116">**平臺：** 查看 [系統需求](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="3e714-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="3e714-117">**標頭：** 以上</span><span class="sxs-lookup"><span data-stu-id="3e714-117">**Header:** None\</span></span>
<span data-ttu-id="3e714-118">連結 **庫：** 以上</span><span class="sxs-lookup"><span data-stu-id="3e714-118">**Library:** None\</span></span>
<span data-ttu-id="3e714-119">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e714-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3e714-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e714-120">See also</span></span>

- [<span data-ttu-id="3e714-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="3e714-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="3e714-122">IXCLRDataProcess 介面</span><span class="sxs-lookup"><span data-stu-id="3e714-122">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
