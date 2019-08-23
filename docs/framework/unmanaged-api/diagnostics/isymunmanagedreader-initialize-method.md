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
ms.openlocfilehash: f2dceeb2f0b3aa9f3147157e77087dffbf2d5f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939018"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="da5dd-102">ISymUnmanagedReader::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="da5dd-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="da5dd-103">使用與此讀取器相關聯的中繼資料匯入介面, 以及模組的檔案名, 初始化符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="da5dd-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da5dd-104">這個方法只能呼叫一次, 而且必須在任何其他讀取器方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="da5dd-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da5dd-105">語法</span><span class="sxs-lookup"><span data-stu-id="da5dd-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da5dd-106">參數</span><span class="sxs-lookup"><span data-stu-id="da5dd-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="da5dd-107">在與這個讀取器相關聯的中繼資料匯入工具介面。</span><span class="sxs-lookup"><span data-stu-id="da5dd-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="da5dd-108">在模組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="da5dd-108">[in] The file name of the module.</span></span> <span data-ttu-id="da5dd-109">您可以`pIStream`改用參數。</span><span class="sxs-lookup"><span data-stu-id="da5dd-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="da5dd-110">在要搜尋的路徑。</span><span class="sxs-lookup"><span data-stu-id="da5dd-110">[in] The path to search.</span></span> <span data-ttu-id="da5dd-111">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="da5dd-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="da5dd-112">在檔案資料流程, 用來做為 filename 參數的替代項。</span><span class="sxs-lookup"><span data-stu-id="da5dd-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da5dd-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="da5dd-113">Return Value</span></span>  
 <span data-ttu-id="da5dd-114">如果方法成功, 則為 S_OK;否則, E_FAIL 或其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="da5dd-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da5dd-115">備註</span><span class="sxs-lookup"><span data-stu-id="da5dd-115">Remarks</span></span>  
 <span data-ttu-id="da5dd-116">您只需要指定其中一個`filename` `pIStream`或參數, 而不是兩者。</span><span class="sxs-lookup"><span data-stu-id="da5dd-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="da5dd-117">`searchPath` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="da5dd-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da5dd-118">需求</span><span class="sxs-lookup"><span data-stu-id="da5dd-118">Requirements</span></span>  
 <span data-ttu-id="da5dd-119">**標頭：** CorSym .idl, CorSym。h</span><span class="sxs-lookup"><span data-stu-id="da5dd-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5dd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da5dd-120">See also</span></span>

- [<span data-ttu-id="da5dd-121">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="da5dd-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
