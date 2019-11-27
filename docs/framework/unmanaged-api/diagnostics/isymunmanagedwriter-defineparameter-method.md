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
ms.openlocfilehash: bc1b65de026a674a3dff183050a5a205fd7052c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428003"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="c92cf-102">ISymUnmanagedWriter::DefineParameter 方法</span><span class="sxs-lookup"><span data-stu-id="c92cf-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="c92cf-103">定義目前方法中的單一參數。</span><span class="sxs-lookup"><span data-stu-id="c92cf-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="c92cf-104">參數類型取自方法簽章中的參數位置（sequence）。</span><span class="sxs-lookup"><span data-stu-id="c92cf-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="c92cf-105">如果在指定方法的中繼資料中定義了參數，您就不需要使用這個方法再次定義它們。</span><span class="sxs-lookup"><span data-stu-id="c92cf-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="c92cf-106">符號讀取器必須先檢查參數的一般中繼資料，然後再檢查符號存放區。</span><span class="sxs-lookup"><span data-stu-id="c92cf-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92cf-107">語法</span><span class="sxs-lookup"><span data-stu-id="c92cf-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c92cf-108">參數</span><span class="sxs-lookup"><span data-stu-id="c92cf-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c92cf-109">在參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c92cf-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="c92cf-110">在參數屬性。</span><span class="sxs-lookup"><span data-stu-id="c92cf-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="c92cf-111">在參數簽章。</span><span class="sxs-lookup"><span data-stu-id="c92cf-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="c92cf-112">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="c92cf-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="c92cf-113">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="c92cf-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="c92cf-114">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="c92cf-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="c92cf-115">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="c92cf-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c92cf-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="c92cf-116">Return Value</span></span>  
 <span data-ttu-id="c92cf-117">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c92cf-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c92cf-118">需求</span><span class="sxs-lookup"><span data-stu-id="c92cf-118">Requirements</span></span>  
 <span data-ttu-id="c92cf-119">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c92cf-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92cf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c92cf-120">See also</span></span>

- [<span data-ttu-id="c92cf-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c92cf-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
