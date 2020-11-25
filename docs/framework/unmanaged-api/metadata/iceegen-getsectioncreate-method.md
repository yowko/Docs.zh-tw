---
title: ICeeGen::GetSectionCreate 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 4ef3992d840f539ca07c411c2d740fa32b14edbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722943"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="1b8fe-102">ICeeGen::GetSectionCreate 方法</span><span class="sxs-lookup"><span data-stu-id="1b8fe-102">ICeeGen::GetSectionCreate Method</span></span>

<span data-ttu-id="1b8fe-103">使用指定的名稱和旗標值，產生並取得程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="1b8fe-104">這個方法已經過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8fe-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b8fe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b8fe-106">參數</span><span class="sxs-lookup"><span data-stu-id="1b8fe-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="1b8fe-107">在字串的指標，指定要建立之區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="1b8fe-108">在指定選項的旗標。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="1b8fe-109">擴展新建立的程式碼區段指標。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b8fe-110">備註</span><span class="sxs-lookup"><span data-stu-id="1b8fe-110">Remarks</span></span>  

 <span data-ttu-id="1b8fe-111">`GetSectionCreate`只有當您有不是由其他方法處理的特殊區段需求時，才需要呼叫。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b8fe-112">需求</span><span class="sxs-lookup"><span data-stu-id="1b8fe-112">Requirements</span></span>  

 <span data-ttu-id="1b8fe-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b8fe-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b8fe-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1b8fe-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b8fe-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1b8fe-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b8fe-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b8fe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b8fe-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b8fe-117">See also</span></span>

- [<span data-ttu-id="1b8fe-118">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="1b8fe-118">ICeeGen Interface</span></span>](iceegen-interface.md)
