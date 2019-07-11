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
ms.openlocfilehash: 6081e2dfd64625697295f2ea2d1560bc597838da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776865"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="ea3bc-102">ISymUnmanagedBinder::GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="ea3bc-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="ea3bc-103">提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="ea3bc-104">這個方法會開啟程式資料庫 (PDB) 檔案，才可執行檔的檔案旁邊。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="ea3bc-105">這項變更已基於安全性考量。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-105">This change has been made for security purposes.</span></span> <span data-ttu-id="ea3bc-106">如果您需要更廣泛的搜尋，對 PDB 檔案時，使用[ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea3bc-107">語法</span><span class="sxs-lookup"><span data-stu-id="ea3bc-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea3bc-108">參數</span><span class="sxs-lookup"><span data-stu-id="ea3bc-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="ea3bc-109">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ea3bc-110">[in]檔案名稱指標。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ea3bc-111">[in]加入搜尋路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ea3bc-112">[out]設定指標所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea3bc-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ea3bc-113">Return Value</span></span>  
 <span data-ttu-id="ea3bc-114">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea3bc-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea3bc-115">需求</span><span class="sxs-lookup"><span data-stu-id="ea3bc-115">Requirements</span></span>  
 <span data-ttu-id="ea3bc-116">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea3bc-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea3bc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea3bc-117">See also</span></span>

- [<span data-ttu-id="ea3bc-118">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="ea3bc-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="ea3bc-119">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="ea3bc-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
