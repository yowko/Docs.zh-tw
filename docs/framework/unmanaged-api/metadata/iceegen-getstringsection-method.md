---
title: ICeeGen::GetStringSection 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
ms.openlocfilehash: bd284bced625de39791377a9248796ca3dd76f5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722917"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="b1b41-102">ICeeGen::GetStringSection 方法</span><span class="sxs-lookup"><span data-stu-id="b1b41-102">ICeeGen::GetStringSection Method</span></span>

<span data-ttu-id="b1b41-103">取得指定之控制碼所參考之程式碼區段的字串表示。</span><span class="sxs-lookup"><span data-stu-id="b1b41-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="b1b41-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="b1b41-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b41-105">語法</span><span class="sxs-lookup"><span data-stu-id="b1b41-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1b41-106">參數</span><span class="sxs-lookup"><span data-stu-id="b1b41-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="b1b41-107">[in，out]程式碼區段的控制碼。</span><span class="sxs-lookup"><span data-stu-id="b1b41-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1b41-108">需求</span><span class="sxs-lookup"><span data-stu-id="b1b41-108">Requirements</span></span>  

 <span data-ttu-id="b1b41-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1b41-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b41-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b1b41-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1b41-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b1b41-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1b41-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b41-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b41-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1b41-113">See also</span></span>

- [<span data-ttu-id="b1b41-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="b1b41-114">ICeeGen Interface</span></span>](iceegen-interface.md)
