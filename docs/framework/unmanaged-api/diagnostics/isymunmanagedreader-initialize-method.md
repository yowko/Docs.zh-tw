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
ms.openlocfilehash: 07d2de5d12fd769cb5cce243d9e721bb6fc185a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615471"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="9fc80-102">ISymUnmanagedReader::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="9fc80-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="9fc80-103">使用與此讀取器相關聯的中繼資料匯入介面，以及模組的檔案名，初始化符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="9fc80-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fc80-104">這個方法只能呼叫一次，而且必須在任何其他讀取器方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="9fc80-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc80-105">語法</span><span class="sxs-lookup"><span data-stu-id="9fc80-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fc80-106">參數</span><span class="sxs-lookup"><span data-stu-id="9fc80-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="9fc80-107">在與這個讀取器相關聯的中繼資料匯入工具介面。</span><span class="sxs-lookup"><span data-stu-id="9fc80-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="9fc80-108">在模組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="9fc80-108">[in] The file name of the module.</span></span> <span data-ttu-id="9fc80-109">您可以改用 `pIStream` 參數。</span><span class="sxs-lookup"><span data-stu-id="9fc80-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="9fc80-110">在要搜尋的路徑。</span><span class="sxs-lookup"><span data-stu-id="9fc80-110">[in] The path to search.</span></span> <span data-ttu-id="9fc80-111">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="9fc80-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="9fc80-112">在檔案資料流程，用來做為 filename 參數的替代項。</span><span class="sxs-lookup"><span data-stu-id="9fc80-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fc80-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="9fc80-113">Return Value</span></span>  
 <span data-ttu-id="9fc80-114">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9fc80-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fc80-115">備註</span><span class="sxs-lookup"><span data-stu-id="9fc80-115">Remarks</span></span>  
 <span data-ttu-id="9fc80-116">您只需要指定其中一個 `filename` 或 `pIStream` 參數，而不是兩者。</span><span class="sxs-lookup"><span data-stu-id="9fc80-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="9fc80-117">`searchPath` 是選用參數。</span><span class="sxs-lookup"><span data-stu-id="9fc80-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc80-118">需求</span><span class="sxs-lookup"><span data-stu-id="9fc80-118">Requirements</span></span>  
 <span data-ttu-id="9fc80-119">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9fc80-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc80-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fc80-120">See also</span></span>

- [<span data-ttu-id="9fc80-121">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="9fc80-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
