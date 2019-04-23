---
title: IMetaDataImport2::GetVersionString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a01b4203145f6ffee4e3a11a3526f0b83e3dc741
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154618"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="03869-102">IMetaDataImport2::GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="03869-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="03869-103">取得執行階段用來建置組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="03869-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03869-104">語法</span><span class="sxs-lookup"><span data-stu-id="03869-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03869-105">參數</span><span class="sxs-lookup"><span data-stu-id="03869-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="03869-106">[out]將指定版本的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="03869-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="03869-107">[in]大小，以寬字元為單位的`pwzBuf`陣列。</span><span class="sxs-lookup"><span data-stu-id="03869-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="03869-108">[out]中的寬字元數目，包括 null 結束字元，傳回`pwzBuf`陣列。</span><span class="sxs-lookup"><span data-stu-id="03869-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03869-109">備註</span><span class="sxs-lookup"><span data-stu-id="03869-109">Remarks</span></span>  
 <span data-ttu-id="03869-110">`GetVersionString`方法會取得目前的中繼資料範圍的內建的版本。</span><span class="sxs-lookup"><span data-stu-id="03869-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="03869-111">如果未曾儲存範圍，不會有內建的版本中，並會傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="03869-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03869-112">需求</span><span class="sxs-lookup"><span data-stu-id="03869-112">Requirements</span></span>  
 <span data-ttu-id="03869-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03869-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03869-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03869-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03869-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="03869-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03869-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03869-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03869-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03869-117">See also</span></span>

- [<span data-ttu-id="03869-118">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="03869-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="03869-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="03869-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
