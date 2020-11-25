---
title: IMetaDataEmit::SetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 236fc848087f64c2327c2c9e790065cc3f64dc58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704301"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="863cb-102">IMetaDataEmit::SetPinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="863cb-102">IMetaDataEmit::SetPinvokeMap Method</span></span>

<span data-ttu-id="863cb-103">設定或變更方法的 PInvoke 簽章的功能，如先前對 IMetaDataEmit 的呼叫所定義 [：:D efinepinvokemap](imetadataemit-definepinvokemap-method.md)。</span><span class="sxs-lookup"><span data-stu-id="863cb-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="863cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="863cb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="863cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="863cb-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="863cb-106">在 `mdToken` 要套用對應資訊的。</span><span class="sxs-lookup"><span data-stu-id="863cb-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="863cb-107">在PInvoke 用來進行對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="863cb-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="863cb-108">這是值的位元遮罩 `CorPinvokeMap` 。</span><span class="sxs-lookup"><span data-stu-id="863cb-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="863cb-109">在原生 DLL 中的目標匯出名稱。</span><span class="sxs-lookup"><span data-stu-id="863cb-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="863cb-110">在 `mdModuleRef` 目標非受控 DLL 的標記。</span><span class="sxs-lookup"><span data-stu-id="863cb-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="863cb-111">需求</span><span class="sxs-lookup"><span data-stu-id="863cb-111">Requirements</span></span>  

 <span data-ttu-id="863cb-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="863cb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="863cb-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="863cb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="863cb-114">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="863cb-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="863cb-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="863cb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863cb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="863cb-116">See also</span></span>

- [<span data-ttu-id="863cb-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="863cb-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="863cb-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="863cb-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
