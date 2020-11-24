---
title: IMetaDataTables::GetString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 8ecaa003084064be1071a85aa726c38d773ec0b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672574"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="dcef7-102">IMetaDataTables::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="dcef7-102">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="dcef7-103">從目前參考範圍中的資料表資料行取得位於指定索引位置的字串。</span><span class="sxs-lookup"><span data-stu-id="dcef7-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcef7-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcef7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcef7-105">參數</span><span class="sxs-lookup"><span data-stu-id="dcef7-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="dcef7-106">在要開始搜尋下一個值的索引。</span><span class="sxs-lookup"><span data-stu-id="dcef7-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="dcef7-107">擴展傳回之字串值指標的指標。</span><span class="sxs-lookup"><span data-stu-id="dcef7-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcef7-108">需求</span><span class="sxs-lookup"><span data-stu-id="dcef7-108">Requirements</span></span>  

 <span data-ttu-id="dcef7-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcef7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcef7-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="dcef7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcef7-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="dcef7-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcef7-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcef7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcef7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcef7-113">See also</span></span>

- [<span data-ttu-id="dcef7-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="dcef7-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="dcef7-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="dcef7-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
