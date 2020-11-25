---
title: IAssemblyName::GetName 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 58b8b83ce1db9338612cbaa01a0db0862cf1054e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727896"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="17ad4-102">IAssemblyName::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="17ad4-102">IAssemblyName::GetName Method</span></span>

<span data-ttu-id="17ad4-103">取得這個 [IAssemblyName](iassemblyname-interface.md) 物件所參考之元件的簡單、未加密的名稱。</span><span class="sxs-lookup"><span data-stu-id="17ad4-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ad4-104">語法</span><span class="sxs-lookup"><span data-stu-id="17ad4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17ad4-105">參數</span><span class="sxs-lookup"><span data-stu-id="17ad4-105">Parameters</span></span>  

 `lpcwBuffer`  
 <span data-ttu-id="17ad4-106">[in，out] `pwzName` 以寬字元為單位的大小，包括 null 結束字元字元。</span><span class="sxs-lookup"><span data-stu-id="17ad4-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="17ad4-107">擴展保存參考元件名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="17ad4-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17ad4-108">需求</span><span class="sxs-lookup"><span data-stu-id="17ad4-108">Requirements</span></span>  

 <span data-ttu-id="17ad4-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17ad4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ad4-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="17ad4-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="17ad4-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ad4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ad4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17ad4-112">See also</span></span>

- [<span data-ttu-id="17ad4-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="17ad4-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
