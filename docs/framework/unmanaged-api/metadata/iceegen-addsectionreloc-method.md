---
title: ICeeGen::AddSectionReloc 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 2f66d34fcfdd8c61dcc92817ec1a928ac5b603fc
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008894"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="17c33-102">ICeeGen::AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="17c33-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="17c33-103">將 reloc 指令新增至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="17c33-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="17c33-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="17c33-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c33-105">語法</span><span class="sxs-lookup"><span data-stu-id="17c33-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17c33-106">參數</span><span class="sxs-lookup"><span data-stu-id="17c33-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="17c33-107">在要加入 reloc 指令的記憶體內部程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="17c33-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="17c33-108">在區段的位移。</span><span class="sxs-lookup"><span data-stu-id="17c33-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="17c33-109">在參考的區段 `offset` 。</span><span class="sxs-lookup"><span data-stu-id="17c33-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="17c33-110">在其中一個[CeeSectionRelocType](ceesectionreloctype-enumeration.md)值，表示要新增的 reloc 指令類型。</span><span class="sxs-lookup"><span data-stu-id="17c33-110">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17c33-111">需求</span><span class="sxs-lookup"><span data-stu-id="17c33-111">Requirements</span></span>  
 <span data-ttu-id="17c33-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17c33-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17c33-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="17c33-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17c33-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="17c33-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17c33-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17c33-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c33-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17c33-116">See also</span></span>

- [<span data-ttu-id="17c33-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="17c33-117">ICeeGen Interface</span></span>](iceegen-interface.md)
