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
ms.openlocfilehash: 674089f8a1076342a2479c64e253b7dda53ade87
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615198"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="2b6b6-102">ISymUnmanagedWriter::DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="2b6b6-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="2b6b6-103">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b6b6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2b6b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b6b6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2b6b6-106">在的指標 `WCHAR` ，定義全域變數名稱。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="2b6b6-107">在全域變數屬性。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="2b6b6-108">在， `ULONG32` 指出緩衝區的大小（以字元為單位） `signature` 。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="2b6b6-109">在全域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="2b6b6-110">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="2b6b6-111">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="2b6b6-112">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="2b6b6-113">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b6b6-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b6b6-114">Return Value</span></span>  
 <span data-ttu-id="2b6b6-115">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2b6b6-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b6b6-116">需求</span><span class="sxs-lookup"><span data-stu-id="2b6b6-116">Requirements</span></span>  
 <span data-ttu-id="2b6b6-117">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2b6b6-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6b6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b6b6-118">See also</span></span>

- [<span data-ttu-id="2b6b6-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="2b6b6-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="2b6b6-120">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="2b6b6-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="2b6b6-121">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="2b6b6-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
