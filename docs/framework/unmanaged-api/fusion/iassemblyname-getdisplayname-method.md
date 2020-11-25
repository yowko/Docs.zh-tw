---
title: IAssemblyName::GetDisplayName 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727909"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="b68db-102">IAssemblyName::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="b68db-102">IAssemblyName::GetDisplayName Method</span></span>

<span data-ttu-id="b68db-103">取得這個 [IAssemblyName](iassemblyname-interface.md) 物件所參考之元件的人類可讀取名稱。</span><span class="sxs-lookup"><span data-stu-id="b68db-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68db-104">語法</span><span class="sxs-lookup"><span data-stu-id="b68db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b68db-105">參數</span><span class="sxs-lookup"><span data-stu-id="b68db-105">Parameters</span></span>  

 `szDisplayName`  
 <span data-ttu-id="b68db-106">擴展字串緩衝區，其中包含參考元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b68db-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="b68db-107">[in，out] `szDisplayName` 以寬字元為單位的大小，包括 null 結束字元字元。</span><span class="sxs-lookup"><span data-stu-id="b68db-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="b68db-108">在 [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) 值的位元組合，這些值會影響的功能 `szDisplayName` 。</span><span class="sxs-lookup"><span data-stu-id="b68db-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68db-109">需求</span><span class="sxs-lookup"><span data-stu-id="b68db-109">Requirements</span></span>  

 <span data-ttu-id="b68db-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b68db-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68db-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="b68db-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b68db-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68db-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68db-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68db-113">See also</span></span>

- [<span data-ttu-id="b68db-114">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="b68db-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="b68db-115">融合列舉</span><span class="sxs-lookup"><span data-stu-id="b68db-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
