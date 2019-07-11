---
title: ISymUnmanagedReader::UpdateSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfc4507557102e19d95f1b746b3a76a231882d7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736738"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="24894-102">ISymUnmanagedReader::UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="24894-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="24894-103">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="24894-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="24894-104">這個方法用於編輯後繼續的案例中，以更新以符合原始可攜式執行檔 (PE) 的差異符號存放區。</span><span class="sxs-lookup"><span data-stu-id="24894-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24894-105">您需要指定的其中之一`filename`或`pIStream`不可同時為兩者的參數。</span><span class="sxs-lookup"><span data-stu-id="24894-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="24894-106">如果`filename`指定符號存放區將會更新該檔案中的符號。</span><span class="sxs-lookup"><span data-stu-id="24894-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="24894-107">如果`pIStream`未指定，將使用中的資料更新存放區<xref:System.Runtime.InteropServices.ComTypes.IStream>。</span><span class="sxs-lookup"><span data-stu-id="24894-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24894-108">語法</span><span class="sxs-lookup"><span data-stu-id="24894-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24894-109">參數</span><span class="sxs-lookup"><span data-stu-id="24894-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="24894-110">[in]包含符號存放區的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="24894-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="24894-111">[in]檔案資料流，做為替代`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="24894-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24894-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="24894-112">Return Value</span></span>  
 <span data-ttu-id="24894-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="24894-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24894-114">需求</span><span class="sxs-lookup"><span data-stu-id="24894-114">Requirements</span></span>  
 <span data-ttu-id="24894-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="24894-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24894-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24894-116">See also</span></span>

- [<span data-ttu-id="24894-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="24894-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
