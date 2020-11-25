---
title: IMetaDataAssemblyImport::GetAssemblyFromScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: dc40b4a7cf61f8d6141b8e3e57c5e13fe2261b35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731562"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="46bef-102">IMetaDataAssemblyImport::GetAssemblyFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="46bef-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>

<span data-ttu-id="46bef-103">取得目前範圍中元件的指標。</span><span class="sxs-lookup"><span data-stu-id="46bef-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46bef-104">語法</span><span class="sxs-lookup"><span data-stu-id="46bef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46bef-105">參數</span><span class="sxs-lookup"><span data-stu-id="46bef-105">Parameters</span></span>  

 `ptkAssembly`  
 <span data-ttu-id="46bef-106">擴展識別元件之已抓取 `mdAssembly` 權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="46bef-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46bef-107">需求</span><span class="sxs-lookup"><span data-stu-id="46bef-107">Requirements</span></span>  

 <span data-ttu-id="46bef-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46bef-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46bef-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="46bef-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46bef-110">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="46bef-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46bef-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46bef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46bef-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46bef-112">See also</span></span>

- [<span data-ttu-id="46bef-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="46bef-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
