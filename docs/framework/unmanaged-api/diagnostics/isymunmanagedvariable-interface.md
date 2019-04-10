---
title: ISymUnmanagedVariable 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 712eca7f3f9fec9c81e638802f5a664ec6469d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164342"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="d8afc-102">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="d8afc-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="d8afc-103">表示變數，例如參數、 區域變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="d8afc-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8afc-104">方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-104">Methods</span></span>  
  
|<span data-ttu-id="d8afc-105">方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-105">Method</span></span>|<span data-ttu-id="d8afc-106">描述</span><span class="sxs-lookup"><span data-stu-id="d8afc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8afc-107">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="d8afc-108">取得這個變數中的第一個 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="d8afc-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="d8afc-109">其意義取決於位址的類型。</span><span class="sxs-lookup"><span data-stu-id="d8afc-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="d8afc-110">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="d8afc-111">取得這個變數中的第二個 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="d8afc-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="d8afc-112">其意義取決於位址的類型。</span><span class="sxs-lookup"><span data-stu-id="d8afc-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="d8afc-113">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="d8afc-114">取得這個變數中的第三個的 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="d8afc-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="d8afc-115">其意義取決於位址的類型。</span><span class="sxs-lookup"><span data-stu-id="d8afc-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="d8afc-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="d8afc-117">取得地址，這個變數的種類。</span><span class="sxs-lookup"><span data-stu-id="d8afc-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="d8afc-118">GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="d8afc-119">取得此變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="d8afc-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="d8afc-120">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="d8afc-121">取得其父系內這個變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="d8afc-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="d8afc-122">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="d8afc-123">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8afc-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="d8afc-124">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="d8afc-125">取得這個變數的簽章。</span><span class="sxs-lookup"><span data-stu-id="d8afc-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="d8afc-126">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d8afc-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="d8afc-127">取得這個變數，其父系內的起始位移。</span><span class="sxs-lookup"><span data-stu-id="d8afc-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8afc-128">需求</span><span class="sxs-lookup"><span data-stu-id="d8afc-128">Requirements</span></span>  
 <span data-ttu-id="d8afc-129">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d8afc-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8afc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8afc-130">See also</span></span>

- [<span data-ttu-id="d8afc-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d8afc-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
