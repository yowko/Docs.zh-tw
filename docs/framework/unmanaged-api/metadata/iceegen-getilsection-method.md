---
title: ICeeGen::GetIlSection 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: c179d5e1ca976d8f425e7c408ceb663cba64f641
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715335"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="e7a42-102">ICeeGen::GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="e7a42-102">ICeeGen::GetIlSection Method</span></span>

<span data-ttu-id="e7a42-103">取得指定之控制碼所參考的中繼語言程式碼基底區段。</span><span class="sxs-lookup"><span data-stu-id="e7a42-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="e7a42-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="e7a42-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a42-105">語法</span><span class="sxs-lookup"><span data-stu-id="e7a42-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7a42-106">參數</span><span class="sxs-lookup"><span data-stu-id="e7a42-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="e7a42-107">在要取得之區段的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e7a42-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a42-108">需求</span><span class="sxs-lookup"><span data-stu-id="e7a42-108">Requirements</span></span>  

 <span data-ttu-id="e7a42-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a42-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a42-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e7a42-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7a42-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e7a42-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7a42-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a42-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a42-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a42-113">See also</span></span>

- [<span data-ttu-id="e7a42-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="e7a42-114">ICeeGen Interface</span></span>](iceegen-interface.md)
