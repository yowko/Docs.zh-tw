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
ms.openlocfilehash: 6670d985eed4c55550b23d3f4110ee20f3b75661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675824"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="bce07-102">ISymUnmanagedReader::UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="bce07-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>

<span data-ttu-id="bce07-103">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="bce07-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="bce07-104">在編輯後繼續案例中，會使用這個方法來更新符號存放區，使其符合原始可攜式可執行檔 (PE) 檔的差異。</span><span class="sxs-lookup"><span data-stu-id="bce07-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bce07-105">您只需指定其中一個 `filename` 或 `pIStream` 參數，不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="bce07-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="bce07-106">如果 `filename` 指定了，則會使用該檔案中的符號來更新符號存放區。</span><span class="sxs-lookup"><span data-stu-id="bce07-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="bce07-107">如果 `pIStream` 指定了，則會使用中的資料來更新存放區 <xref:System.Runtime.InteropServices.ComTypes.IStream> 。</span><span class="sxs-lookup"><span data-stu-id="bce07-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bce07-108">語法</span><span class="sxs-lookup"><span data-stu-id="bce07-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bce07-109">參數</span><span class="sxs-lookup"><span data-stu-id="bce07-109">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="bce07-110">在包含符號存放區的檔案名。</span><span class="sxs-lookup"><span data-stu-id="bce07-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="bce07-111">在檔案資料流程，用來做為參數的替代項 `filename` 。</span><span class="sxs-lookup"><span data-stu-id="bce07-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bce07-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="bce07-112">Return Value</span></span>  

 <span data-ttu-id="bce07-113">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bce07-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bce07-114">需求</span><span class="sxs-lookup"><span data-stu-id="bce07-114">Requirements</span></span>  

 <span data-ttu-id="bce07-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bce07-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce07-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce07-116">See also</span></span>

- [<span data-ttu-id="bce07-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="bce07-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
