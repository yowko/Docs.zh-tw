---
title: ICeeGen::EmitString 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: b9c907868df31da8d995c6a6b86db258d395335d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715442"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="5f22e-102">ICeeGen::EmitString 方法</span><span class="sxs-lookup"><span data-stu-id="5f22e-102">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="5f22e-103">將指定的字串發出至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="5f22e-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="5f22e-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="5f22e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f22e-105">語法</span><span class="sxs-lookup"><span data-stu-id="5f22e-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f22e-106">參數</span><span class="sxs-lookup"><span data-stu-id="5f22e-106">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="5f22e-107">在要發出的字串。</span><span class="sxs-lookup"><span data-stu-id="5f22e-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="5f22e-108">擴展發出之字串的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="5f22e-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f22e-109">需求</span><span class="sxs-lookup"><span data-stu-id="5f22e-109">Requirements</span></span>  

 <span data-ttu-id="5f22e-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f22e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f22e-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5f22e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f22e-112">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5f22e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f22e-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f22e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f22e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f22e-114">See also</span></span>

- [<span data-ttu-id="5f22e-115">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="5f22e-115">ICeeGen Interface</span></span>](iceegen-interface.md)
