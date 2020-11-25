---
title: IMetaDataEmit::SetModuleProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 1757662d2004dce3156182c35b37237ff91bae7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730335"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="83a51-102">IMetaDataEmit::SetModuleProps 方法</span><span class="sxs-lookup"><span data-stu-id="83a51-102">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="83a51-103">更新對 IMetaDataEmit 進行之前呼叫所定義之模組的參考 [：:D efinemoduleref](imetadataemit-definemoduleref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="83a51-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a51-104">語法</span><span class="sxs-lookup"><span data-stu-id="83a51-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a51-105">參數</span><span class="sxs-lookup"><span data-stu-id="83a51-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="83a51-106">在Unicode 中的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="83a51-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="83a51-107">這是唯一的檔案名，而不是完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="83a51-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a51-108">需求</span><span class="sxs-lookup"><span data-stu-id="83a51-108">Requirements</span></span>  

 <span data-ttu-id="83a51-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83a51-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a51-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="83a51-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83a51-111">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="83a51-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83a51-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a51-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a51-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83a51-113">See also</span></span>

- [<span data-ttu-id="83a51-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="83a51-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="83a51-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="83a51-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
