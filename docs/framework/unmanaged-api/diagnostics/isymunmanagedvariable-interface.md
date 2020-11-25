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
ms.openlocfilehash: 93e1f8eb17f06e42ddb243f88c593979fcb28030
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733278"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="f961a-102">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="f961a-102">ISymUnmanagedVariable Interface</span></span>

<span data-ttu-id="f961a-103">代表變數，例如參數、區域變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="f961a-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f961a-104">方法</span><span class="sxs-lookup"><span data-stu-id="f961a-104">Methods</span></span>  
  
|<span data-ttu-id="f961a-105">方法</span><span class="sxs-lookup"><span data-stu-id="f961a-105">Method</span></span>|<span data-ttu-id="f961a-106">描述</span><span class="sxs-lookup"><span data-stu-id="f961a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f961a-107">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="f961a-108">取得這個變數的第一個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="f961a-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="f961a-109">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="f961a-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="f961a-110">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="f961a-111">取得這個變數的第二個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="f961a-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="f961a-112">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="f961a-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="f961a-113">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="f961a-114">取得這個變數的第三個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="f961a-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="f961a-115">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="f961a-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="f961a-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="f961a-117">取得這個變數的位址種類。</span><span class="sxs-lookup"><span data-stu-id="f961a-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="f961a-118">GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="f961a-119">取得這個變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="f961a-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="f961a-120">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="f961a-121">取得此變數在其父系內的結束位移。</span><span class="sxs-lookup"><span data-stu-id="f961a-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="f961a-122">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="f961a-123">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="f961a-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="f961a-124">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="f961a-125">取得這個變數的簽章。</span><span class="sxs-lookup"><span data-stu-id="f961a-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="f961a-126">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f961a-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="f961a-127">取得此變數在其父系內的開始位移。</span><span class="sxs-lookup"><span data-stu-id="f961a-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f961a-128">需求</span><span class="sxs-lookup"><span data-stu-id="f961a-128">Requirements</span></span>  

 <span data-ttu-id="f961a-129">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="f961a-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f961a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f961a-130">See also</span></span>

- [<span data-ttu-id="f961a-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="f961a-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
