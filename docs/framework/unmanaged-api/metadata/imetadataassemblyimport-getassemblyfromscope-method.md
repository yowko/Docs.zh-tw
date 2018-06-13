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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7322b4d0fce36f5dbef7e82f35cf9e2a1cae24a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444326"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="b3b9a-102">IMetaDataAssemblyImport::GetAssemblyFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="b3b9a-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="b3b9a-103">取得目前範圍中的組件的指標。</span><span class="sxs-lookup"><span data-stu-id="b3b9a-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3b9a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3b9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3b9a-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="b3b9a-106">[out]所擷取的指標`mdAssembly`識別的組件的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b3b9a-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b9a-107">需求</span><span class="sxs-lookup"><span data-stu-id="b3b9a-107">Requirements</span></span>  
 <span data-ttu-id="b3b9a-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b9a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b9a-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3b9a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3b9a-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3b9a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3b9a-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b9a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b9a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3b9a-112">See Also</span></span>  
 [<span data-ttu-id="b3b9a-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="b3b9a-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
