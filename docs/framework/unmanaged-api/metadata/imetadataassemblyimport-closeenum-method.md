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
ms.openlocfilehash: d2ce26daa5f5c36e4073eee653cc650c1a8d54c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708928"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="30dff-102">IMetaDataAssemblyImport::CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="30dff-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>

<span data-ttu-id="30dff-103">釋放指定之列舉實例的參考。</span><span class="sxs-lookup"><span data-stu-id="30dff-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30dff-104">語法</span><span class="sxs-lookup"><span data-stu-id="30dff-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30dff-105">參數</span><span class="sxs-lookup"><span data-stu-id="30dff-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="30dff-106">在要關閉的列舉實例。</span><span class="sxs-lookup"><span data-stu-id="30dff-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30dff-107">需求</span><span class="sxs-lookup"><span data-stu-id="30dff-107">Requirements</span></span>  

 <span data-ttu-id="30dff-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30dff-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30dff-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="30dff-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30dff-110">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="30dff-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30dff-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30dff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dff-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30dff-112">See also</span></span>

- [<span data-ttu-id="30dff-113">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="30dff-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
