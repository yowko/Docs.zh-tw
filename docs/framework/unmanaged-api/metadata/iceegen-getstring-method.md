---
title: ICeeGen::GetString 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: 9d14ec33128596a148ca3509a49c8c97fafe82d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723099"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="7f437-102">ICeeGen::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="7f437-102">ICeeGen::GetString Method</span></span>

<span data-ttu-id="7f437-103">取得儲存在指定相對虛擬位址的字串。</span><span class="sxs-lookup"><span data-stu-id="7f437-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="7f437-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="7f437-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f437-105">語法</span><span class="sxs-lookup"><span data-stu-id="7f437-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f437-106">參數</span><span class="sxs-lookup"><span data-stu-id="7f437-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="7f437-107">在要傳回之字串的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="7f437-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="7f437-108">擴展傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="7f437-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f437-109">需求</span><span class="sxs-lookup"><span data-stu-id="7f437-109">Requirements</span></span>  

 <span data-ttu-id="7f437-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f437-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f437-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7f437-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f437-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7f437-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f437-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f437-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f437-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f437-114">See also</span></span>

- [<span data-ttu-id="7f437-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="7f437-115">ICeeGen Interface</span></span>](iceegen-interface.md)
