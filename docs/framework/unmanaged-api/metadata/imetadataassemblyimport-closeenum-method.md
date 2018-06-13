---
title: IMetaDataAssemblyImport::CloseEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5477578491c3cbc3f5fce694820971e99b45079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444096"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="4077c-102">IMetaDataAssemblyImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="4077c-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="4077c-103">釋放指定之列舉的執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="4077c-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4077c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4077c-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4077c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4077c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4077c-106">[in]列舉型別執行個體即將關閉。</span><span class="sxs-lookup"><span data-stu-id="4077c-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4077c-107">需求</span><span class="sxs-lookup"><span data-stu-id="4077c-107">Requirements</span></span>  
 <span data-ttu-id="4077c-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4077c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4077c-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4077c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4077c-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4077c-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4077c-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4077c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4077c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4077c-112">See Also</span></span>  
 [<span data-ttu-id="4077c-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="4077c-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
