---
title: ICeeGen::AllocateMethodBuffer 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: e1849eb95401e3637a1fd1b00715332f9886071e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715507"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="6c9c1-102">ICeeGen::AllocateMethodBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="6c9c1-102">ICeeGen::AllocateMethodBuffer Method</span></span>

<span data-ttu-id="6c9c1-103">針對方法建立指定大小的緩衝區，並取得方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="6c9c1-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="6c9c1-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="6c9c1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9c1-105">語法</span><span class="sxs-lookup"><span data-stu-id="6c9c1-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c9c1-106">參數</span><span class="sxs-lookup"><span data-stu-id="6c9c1-106">Parameters</span></span>  

 `cchBuffer`  
 <span data-ttu-id="6c9c1-107">在要建立之緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="6c9c1-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="6c9c1-108">擴展傳回的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6c9c1-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="6c9c1-109">擴展方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="6c9c1-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9c1-110">需求</span><span class="sxs-lookup"><span data-stu-id="6c9c1-110">Requirements</span></span>  

 <span data-ttu-id="6c9c1-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c9c1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9c1-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6c9c1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c9c1-113">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6c9c1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c9c1-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9c1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9c1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c9c1-115">See also</span></span>

- [<span data-ttu-id="6c9c1-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="6c9c1-116">ICeeGen Interface</span></span>](iceegen-interface.md)
