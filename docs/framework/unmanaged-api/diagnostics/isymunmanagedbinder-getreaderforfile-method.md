---
title: ISymUnmanagedBinder::GetReaderForFile 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0414cadca910f3290f96a841e3f807f0de469606
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145960"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="5839b-102">ISymUnmanagedBinder::GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="5839b-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="5839b-103">提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="5839b-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="5839b-104">這個方法會開啟程式資料庫 (PDB) 檔案，才可執行檔的檔案旁邊。</span><span class="sxs-lookup"><span data-stu-id="5839b-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="5839b-105">這項變更已基於安全性考量。</span><span class="sxs-lookup"><span data-stu-id="5839b-105">This change has been made for security purposes.</span></span> <span data-ttu-id="5839b-106">如果您需要更廣泛的搜尋，對 PDB 檔案時，使用[ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5839b-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5839b-107">語法</span><span class="sxs-lookup"><span data-stu-id="5839b-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5839b-108">參數</span><span class="sxs-lookup"><span data-stu-id="5839b-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="5839b-109">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="5839b-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="5839b-110">[in]檔案名稱指標。</span><span class="sxs-lookup"><span data-stu-id="5839b-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="5839b-111">[in]加入搜尋路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="5839b-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5839b-112">[out]設定指標所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="5839b-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5839b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="5839b-113">Return Value</span></span>  
 <span data-ttu-id="5839b-114">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5839b-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5839b-115">需求</span><span class="sxs-lookup"><span data-stu-id="5839b-115">Requirements</span></span>  
 <span data-ttu-id="5839b-116">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5839b-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5839b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5839b-117">See also</span></span>

- [<span data-ttu-id="5839b-118">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="5839b-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="5839b-119">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="5839b-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
