---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 923a92ea256f79a1b0130b61c4fd99460fda96a0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441804"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="ec3bb-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="ec3bb-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="ec3bb-103">傳回方法的陣列，其中每一個都包含檔中指定位置的中斷點。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec3bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec3bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec3bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec3bb-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="ec3bb-106">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="ec3bb-107">在指定檔的行。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="ec3bb-108">在指定檔的資料行。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="ec3bb-109">[in] `pRetVal` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="ec3bb-110">脫銷變數的指標，會接收 `pRetVal` 陣列中傳回的元素數目。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ec3bb-111">脫銷指標陣列，其中每一個都會指向代表包含中斷點之方法的[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec3bb-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="ec3bb-112">Return Value</span></span>  
 <span data-ttu-id="ec3bb-113">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ec3bb-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec3bb-114">需求</span><span class="sxs-lookup"><span data-stu-id="ec3bb-114">Requirements</span></span>  
 <span data-ttu-id="ec3bb-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ec3bb-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec3bb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec3bb-116">See also</span></span>

- [<span data-ttu-id="ec3bb-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="ec3bb-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
