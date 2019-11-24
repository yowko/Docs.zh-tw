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
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="b7efc-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="b7efc-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="b7efc-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span><span class="sxs-lookup"><span data-stu-id="b7efc-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7efc-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7efc-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b7efc-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7efc-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b7efc-106">[in] The specified document.</span><span class="sxs-lookup"><span data-stu-id="b7efc-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="b7efc-107">[in] The line of the specified document.</span><span class="sxs-lookup"><span data-stu-id="b7efc-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="b7efc-108">[in] The column of the specified document.</span><span class="sxs-lookup"><span data-stu-id="b7efc-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="b7efc-109">[in] `pRetVal` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="b7efc-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="b7efc-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span><span class="sxs-lookup"><span data-stu-id="b7efc-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b7efc-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span><span class="sxs-lookup"><span data-stu-id="b7efc-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7efc-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7efc-112">Return Value</span></span>  
 <span data-ttu-id="b7efc-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="b7efc-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7efc-114">需求</span><span class="sxs-lookup"><span data-stu-id="b7efc-114">Requirements</span></span>  
 <span data-ttu-id="b7efc-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b7efc-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7efc-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7efc-116">See also</span></span>

- [<span data-ttu-id="b7efc-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="b7efc-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
