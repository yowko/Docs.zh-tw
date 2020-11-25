---
title: ICeeGen::GetSectionDataLen 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: b45b0a59a29a27e7b0a395f3928215959450f9a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698464"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="a7bc6-102">ICeeGen::GetSectionDataLen 方法</span><span class="sxs-lookup"><span data-stu-id="a7bc6-102">ICeeGen::GetSectionDataLen Method</span></span>

<span data-ttu-id="a7bc6-103">取得指定區段的長度。</span><span class="sxs-lookup"><span data-stu-id="a7bc6-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="a7bc6-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="a7bc6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7bc6-105">語法</span><span class="sxs-lookup"><span data-stu-id="a7bc6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7bc6-106">參數</span><span class="sxs-lookup"><span data-stu-id="a7bc6-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="a7bc6-107">在將取出其長度的資料區段。</span><span class="sxs-lookup"><span data-stu-id="a7bc6-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="a7bc6-108">擴展指定區段的傳回長度。</span><span class="sxs-lookup"><span data-stu-id="a7bc6-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7bc6-109">備註</span><span class="sxs-lookup"><span data-stu-id="a7bc6-109">Remarks</span></span>  

 <span data-ttu-id="a7bc6-110">`GetSectionDataLen`只有當您有不是由其他方法處理的特殊區段需求時，才需要呼叫。</span><span class="sxs-lookup"><span data-stu-id="a7bc6-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7bc6-111">需求</span><span class="sxs-lookup"><span data-stu-id="a7bc6-111">Requirements</span></span>  

 <span data-ttu-id="a7bc6-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7bc6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7bc6-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a7bc6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7bc6-114">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a7bc6-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7bc6-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7bc6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7bc6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7bc6-116">See also</span></span>

- [<span data-ttu-id="a7bc6-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="a7bc6-117">ICeeGen Interface</span></span>](iceegen-interface.md)
