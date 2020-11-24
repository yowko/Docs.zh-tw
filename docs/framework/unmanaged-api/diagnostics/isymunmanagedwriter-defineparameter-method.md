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
ms.openlocfilehash: c5e36443295395997303cb94202f534a83d086f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677865"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="c0dd6-102">ISymUnmanagedWriter::DefineParameter 方法</span><span class="sxs-lookup"><span data-stu-id="c0dd6-102">ISymUnmanagedWriter::DefineParameter Method</span></span>

<span data-ttu-id="c0dd6-103">定義目前方法中的單一參數。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="c0dd6-104">參數類型是取自方法簽章中 (序列) 的參數位置。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="c0dd6-105">如果在指定方法的中繼資料中定義參數，則不需要使用這個方法再次定義這些參數。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="c0dd6-106">符號讀取器必須先檢查參數的一般中繼資料，才能檢查符號存放區。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0dd6-107">語法</span><span class="sxs-lookup"><span data-stu-id="c0dd6-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c0dd6-108">參數</span><span class="sxs-lookup"><span data-stu-id="c0dd6-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c0dd6-109">在參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="c0dd6-110">在參數屬性。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="c0dd6-111">在參數簽章。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="c0dd6-112">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="c0dd6-113">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="c0dd6-114">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="c0dd6-115">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0dd6-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="c0dd6-116">Return Value</span></span>  

 <span data-ttu-id="c0dd6-117">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c0dd6-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0dd6-118">需求</span><span class="sxs-lookup"><span data-stu-id="c0dd6-118">Requirements</span></span>  

 <span data-ttu-id="c0dd6-119">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c0dd6-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0dd6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0dd6-120">See also</span></span>

- [<span data-ttu-id="c0dd6-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c0dd6-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
