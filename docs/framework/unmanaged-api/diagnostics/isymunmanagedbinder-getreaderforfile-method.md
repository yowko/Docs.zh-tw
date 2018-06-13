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
ms.openlocfilehash: d4f896dcd78061284416468968ba5a9a5fbbda2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428536"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="19f9d-102">ISymUnmanagedBinder::GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="19f9d-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="19f9d-103">提供中繼資料介面和檔案名稱，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 會讀取偵錯符號的模組相關聯的結構。</span><span class="sxs-lookup"><span data-stu-id="19f9d-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="19f9d-104">這個方法會開啟程式資料庫 (PDB) 檔，才可執行檔的檔案旁邊。</span><span class="sxs-lookup"><span data-stu-id="19f9d-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="19f9d-105">這項變更已經成為基於安全性考量。</span><span class="sxs-lookup"><span data-stu-id="19f9d-105">This change has been made for security purposes.</span></span> <span data-ttu-id="19f9d-106">如果您需要對 PDB 檔案更廣泛的搜尋，請使用[isymunmanagedbinder2:: Getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="19f9d-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f9d-107">語法</span><span class="sxs-lookup"><span data-stu-id="19f9d-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19f9d-108">參數</span><span class="sxs-lookup"><span data-stu-id="19f9d-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="19f9d-109">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="19f9d-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="19f9d-110">[in]指向的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="19f9d-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="19f9d-111">[in]加入搜尋路徑中的指標。</span><span class="sxs-lookup"><span data-stu-id="19f9d-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="19f9d-112">[out]設定的指標所傳回 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 介面。</span><span class="sxs-lookup"><span data-stu-id="19f9d-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19f9d-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="19f9d-113">Return Value</span></span>  
 <span data-ttu-id="19f9d-114">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="19f9d-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19f9d-115">需求</span><span class="sxs-lookup"><span data-stu-id="19f9d-115">Requirements</span></span>  
 <span data-ttu-id="19f9d-116">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="19f9d-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f9d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19f9d-117">See Also</span></span>  
 [<span data-ttu-id="19f9d-118">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="19f9d-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="19f9d-119">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="19f9d-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
