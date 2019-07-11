---
title: ISymUnmanagedWriter::DefineParameter 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b82415635980f5bd4e13e87a0a03ec5b7032bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777334"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="1f606-102">ISymUnmanagedWriter::DefineParameter 方法</span><span class="sxs-lookup"><span data-stu-id="1f606-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="1f606-103">目前方法中定義的單一參數。</span><span class="sxs-lookup"><span data-stu-id="1f606-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="1f606-104">參數類型是來自方法的簽章中參數的位置 （序列）。</span><span class="sxs-lookup"><span data-stu-id="1f606-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="1f606-105">指定方法的中繼資料中定義了參數，如果您沒有使用這個方法來重新定義。</span><span class="sxs-lookup"><span data-stu-id="1f606-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="1f606-106">符號讀取器必須檢查符號存放區之前先檢查一般的中繼資料的參數。</span><span class="sxs-lookup"><span data-stu-id="1f606-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f606-107">語法</span><span class="sxs-lookup"><span data-stu-id="1f606-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f606-108">參數</span><span class="sxs-lookup"><span data-stu-id="1f606-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1f606-109">[in]參數名稱。</span><span class="sxs-lookup"><span data-stu-id="1f606-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1f606-110">[in]參數屬性。</span><span class="sxs-lookup"><span data-stu-id="1f606-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="1f606-111">[in]參數簽章。</span><span class="sxs-lookup"><span data-stu-id="1f606-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1f606-112">[in]位址類型。</span><span class="sxs-lookup"><span data-stu-id="1f606-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1f606-113">[in]參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="1f606-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1f606-114">[in]參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="1f606-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1f606-115">[in]參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="1f606-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f606-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="1f606-116">Return Value</span></span>  
 <span data-ttu-id="1f606-117">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f606-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f606-118">需求</span><span class="sxs-lookup"><span data-stu-id="1f606-118">Requirements</span></span>  
 <span data-ttu-id="1f606-119">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f606-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f606-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f606-120">See also</span></span>

- [<span data-ttu-id="1f606-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="1f606-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
