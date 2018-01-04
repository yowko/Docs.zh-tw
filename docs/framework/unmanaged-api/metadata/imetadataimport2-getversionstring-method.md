---
title: "IMetaDataImport2::GetVersionString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccf168473c1182e4b7d57d52930d90084eaa2dd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="ea2d9-102">IMetaDataImport2::GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="ea2d9-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="ea2d9-103">取得執行階段用來建置組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea2d9-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea2d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea2d9-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="ea2d9-106">[out]將指定版本的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="ea2d9-107">[in]大小，以寬字元為單位的`pwzBuf`陣列。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="ea2d9-108">[out]中的寬字元數目，包括 null 結束字元，傳回`pwzBuf`陣列。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2d9-109">備註</span><span class="sxs-lookup"><span data-stu-id="ea2d9-109">Remarks</span></span>  
 <span data-ttu-id="ea2d9-110">`GetVersionString`方法會取得目前中繼資料範圍的內建的版本。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="ea2d9-111">如果從未儲存範圍，則將不會建置的版本中，並會傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2d9-112">需求</span><span class="sxs-lookup"><span data-stu-id="ea2d9-112">Requirements</span></span>  
 <span data-ttu-id="ea2d9-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea2d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2d9-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea2d9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea2d9-115">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ea2d9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea2d9-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2d9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea2d9-117">See Also</span></span>  
 [<span data-ttu-id="ea2d9-118">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ea2d9-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="ea2d9-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ea2d9-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
