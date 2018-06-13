---
title: ISymUnmanagedReader::Initialize 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d141d23f02b2abc92e3d4455aebe1a4057b6bb85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426469"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="76db1-102">ISymUnmanagedReader::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="76db1-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="76db1-103">初始化這個讀取器會與，以及檔案名稱的模組相關聯的中繼資料匯入工具介面的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="76db1-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76db1-104">這個方法可以只一次，而且必須在任何其他的讀取器方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="76db1-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76db1-105">語法</span><span class="sxs-lookup"><span data-stu-id="76db1-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76db1-106">參數</span><span class="sxs-lookup"><span data-stu-id="76db1-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="76db1-107">[in]與這個讀取器將相關聯的中繼資料匯入工具介面。</span><span class="sxs-lookup"><span data-stu-id="76db1-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="76db1-108">[in]模組檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="76db1-108">[in] The file name of the module.</span></span> <span data-ttu-id="76db1-109">您可以使用`pIStream`參數改為。</span><span class="sxs-lookup"><span data-stu-id="76db1-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="76db1-110">[in]要搜尋的路徑。</span><span class="sxs-lookup"><span data-stu-id="76db1-110">[in] The path to search.</span></span> <span data-ttu-id="76db1-111">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="76db1-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="76db1-112">[in]檔案資料流，做為檔案名稱參數的替代方案。</span><span class="sxs-lookup"><span data-stu-id="76db1-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76db1-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="76db1-113">Return Value</span></span>  
 <span data-ttu-id="76db1-114">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="76db1-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76db1-115">備註</span><span class="sxs-lookup"><span data-stu-id="76db1-115">Remarks</span></span>  
 <span data-ttu-id="76db1-116">您必須指定的其中之一`filename`或`pIStream`參數不可同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="76db1-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="76db1-117">`searchPath` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="76db1-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76db1-118">需求</span><span class="sxs-lookup"><span data-stu-id="76db1-118">Requirements</span></span>  
 <span data-ttu-id="76db1-119">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="76db1-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76db1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76db1-120">See Also</span></span>  
 [<span data-ttu-id="76db1-121">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="76db1-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
