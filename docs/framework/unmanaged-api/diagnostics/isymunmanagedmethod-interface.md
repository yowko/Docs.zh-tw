---
title: ISymUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615120"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="056a0-102">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="056a0-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="056a0-103">表示符號存放區中的方法。</span><span class="sxs-lookup"><span data-stu-id="056a0-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="056a0-104">這個介面只提供存取方法的符號相關屬性，而不是與型別相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="056a0-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="056a0-105">方法</span><span class="sxs-lookup"><span data-stu-id="056a0-105">Methods</span></span>  
  
|<span data-ttu-id="056a0-106">方法</span><span class="sxs-lookup"><span data-stu-id="056a0-106">Method</span></span>|<span data-ttu-id="056a0-107">描述</span><span class="sxs-lookup"><span data-stu-id="056a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="056a0-108">GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="056a0-109">取得在其中定義這個方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="056a0-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="056a0-110">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="056a0-111">傳回這個方法內對應于檔內指定位置的位移。</span><span class="sxs-lookup"><span data-stu-id="056a0-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="056a0-112">GetParameters 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="056a0-113">取得這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="056a0-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="056a0-114">GetRanges 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="056a0-115">指定檔中的位置時，會傳回開始和結束位移組的陣列，其對應于此方法內的位置所涵蓋的 Microsoft 中繼語言（MSIL）範圍。</span><span class="sxs-lookup"><span data-stu-id="056a0-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="056a0-116">GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="056a0-117">取得這個方法內的根詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="056a0-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="056a0-118">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="056a0-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="056a0-119">GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="056a0-120">取得在這個方法中，包含指定之位移的最封入詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="056a0-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="056a0-121">GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="056a0-122">取得這個方法內的序列點計數。</span><span class="sxs-lookup"><span data-stu-id="056a0-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="056a0-123">GetSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="056a0-124">取得這個方法內的所有序列點。</span><span class="sxs-lookup"><span data-stu-id="056a0-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="056a0-125">GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="056a0-126">取得這個方法之來源的開始和結束檔位置。</span><span class="sxs-lookup"><span data-stu-id="056a0-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="056a0-127">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="056a0-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="056a0-128">傳回這個方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="056a0-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="056a0-129">需求</span><span class="sxs-lookup"><span data-stu-id="056a0-129">Requirements</span></span>  
 <span data-ttu-id="056a0-130">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="056a0-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056a0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="056a0-131">See also</span></span>

- [<span data-ttu-id="056a0-132">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="056a0-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
