---
title: ISymUnmanagedWriter::DefineGlobalVariable 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: bc389b7247a6b1d6ce16cb3cf350f1672213b2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716417"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="94122-102">ISymUnmanagedWriter::DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="94122-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>

<span data-ttu-id="94122-103">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="94122-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94122-104">語法</span><span class="sxs-lookup"><span data-stu-id="94122-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94122-105">參數</span><span class="sxs-lookup"><span data-stu-id="94122-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="94122-106">在的指標 `WCHAR` ，定義全域變數名稱。</span><span class="sxs-lookup"><span data-stu-id="94122-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="94122-107">在全域變數屬性。</span><span class="sxs-lookup"><span data-stu-id="94122-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="94122-108">在， `ULONG32` 表示緩衝區的大小（以字元為單位） `signature` 。</span><span class="sxs-lookup"><span data-stu-id="94122-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="94122-109">在全域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="94122-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="94122-110">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="94122-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="94122-111">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="94122-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="94122-112">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="94122-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="94122-113">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="94122-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94122-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="94122-114">Return Value</span></span>  

 <span data-ttu-id="94122-115">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="94122-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94122-116">需求</span><span class="sxs-lookup"><span data-stu-id="94122-116">Requirements</span></span>  

 <span data-ttu-id="94122-117">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="94122-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94122-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94122-118">See also</span></span>

- [<span data-ttu-id="94122-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="94122-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="94122-120">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="94122-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="94122-121">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="94122-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
