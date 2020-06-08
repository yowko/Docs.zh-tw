---
title: IMetaDataImport::GetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: 8409e56b5ec4dbe47035a0555b6b7ce175b517ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490974"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="479c6-102">IMetaDataImport::GetPinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="479c6-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="479c6-103">取得 ModuleRef 語彙基元以代表 PInvoke 呼叫的目標組件。</span><span class="sxs-lookup"><span data-stu-id="479c6-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="479c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="479c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="479c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="479c6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="479c6-106">在要取得其 PInvoke 對應中繼資料的 FieldDef 或 MethodDef token。</span><span class="sxs-lookup"><span data-stu-id="479c6-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="479c6-107">脫銷用於對應之旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="479c6-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="479c6-108">這個值是[CorPinvokeMap](corpinvokemap-enumeration.md)列舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="479c6-108">This value is a bitmask from the [CorPinvokeMap](corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="479c6-109">脫銷非受控目標 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="479c6-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="479c6-110">在的大小（以寬字元為單位） `szImportName` 。</span><span class="sxs-lookup"><span data-stu-id="479c6-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="479c6-111">脫銷在中傳回的寬字元數 `szImportName` 。</span><span class="sxs-lookup"><span data-stu-id="479c6-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="479c6-112">脫銷ModuleRef token 的指標，表示非受控目標物件程式庫。</span><span class="sxs-lookup"><span data-stu-id="479c6-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="479c6-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="479c6-113">Requirements</span></span>  
 <span data-ttu-id="479c6-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="479c6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="479c6-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="479c6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="479c6-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="479c6-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="479c6-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="479c6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479c6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="479c6-118">See also</span></span>

- [<span data-ttu-id="479c6-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="479c6-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="479c6-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="479c6-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
