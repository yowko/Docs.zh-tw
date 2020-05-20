---
title: ISymUnmanagedWriter 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: 8f0bbd26bde562df5482d167c9d2775e01426f55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610050"
---
# <a name="isymunmanagedwriter-interface"></a><span data-ttu-id="88ec7-102">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="88ec7-102">ISymUnmanagedWriter Interface</span></span>
<span data-ttu-id="88ec7-103">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="88ec7-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88ec7-104">方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-104">Methods</span></span>  
  
|<span data-ttu-id="88ec7-105">方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-105">Method</span></span>|<span data-ttu-id="88ec7-106">描述</span><span class="sxs-lookup"><span data-stu-id="88ec7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88ec7-107">Abort 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-107">Abort Method</span></span>](isymunmanagedwriter-abort-method.md)|<span data-ttu-id="88ec7-108">關閉符號寫入器，而不將符號認可到符號存放區。</span><span class="sxs-lookup"><span data-stu-id="88ec7-108">Closes the symbol writer without committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="88ec7-109">Close 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-109">Close Method</span></span>](isymunmanagedwriter-close-method.md)|<span data-ttu-id="88ec7-110">將符號認可到符號存放區之後，關閉符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="88ec7-110">Closes the symbol writer after committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="88ec7-111">CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-111">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)|<span data-ttu-id="88ec7-112">關閉目前的方法。</span><span class="sxs-lookup"><span data-stu-id="88ec7-112">Closes the current method.</span></span> <span data-ttu-id="88ec7-113">關閉方法後，就不能在其中定義更多符號。</span><span class="sxs-lookup"><span data-stu-id="88ec7-113">Once a method is closed, no more symbols can be defined within it.</span></span>|  
|[<span data-ttu-id="88ec7-114">CloseNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-114">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)|<span data-ttu-id="88ec7-115">關閉最近開啟的命名空間。</span><span class="sxs-lookup"><span data-stu-id="88ec7-115">Closes the most recently opened namespace.</span></span>|  
|[<span data-ttu-id="88ec7-116">CloseScope 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-116">CloseScope Method</span></span>](isymunmanagedwriter-closescope-method.md)|<span data-ttu-id="88ec7-117">關閉目前的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="88ec7-117">Closes the current lexical scope.</span></span>|  
|[<span data-ttu-id="88ec7-118">DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-118">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)|<span data-ttu-id="88ec7-119">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="88ec7-119">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="88ec7-120">DefineDocument 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-120">DefineDocument Method</span></span>](isymunmanagedwriter-definedocument-method.md)|<span data-ttu-id="88ec7-121">定義來源文件。</span><span class="sxs-lookup"><span data-stu-id="88ec7-121">Defines a source document.</span></span>|  
|[<span data-ttu-id="88ec7-122">DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-122">DefineField Method</span></span>](isymunmanagedwriter-definefield-method.md)|<span data-ttu-id="88ec7-123">定義不在方法內的單一變數。</span><span class="sxs-lookup"><span data-stu-id="88ec7-123">Defines a single variable that is not within a method.</span></span>|  
|[<span data-ttu-id="88ec7-124">DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-124">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)|<span data-ttu-id="88ec7-125">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="88ec7-125">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="88ec7-126">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-126">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)|<span data-ttu-id="88ec7-127">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="88ec7-127">Defines a single variable in the current lexical scope.</span></span>|  
|[<span data-ttu-id="88ec7-128">DefineParameter 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-128">DefineParameter Method</span></span>](isymunmanagedwriter-defineparameter-method.md)|<span data-ttu-id="88ec7-129">定義目前方法中的單一參數。</span><span class="sxs-lookup"><span data-stu-id="88ec7-129">Defines a single parameter in the current method.</span></span>|  
|[<span data-ttu-id="88ec7-130">DefineSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-130">DefineSequencePoints Method</span></span>](isymunmanagedwriter-definesequencepoints-method.md)|<span data-ttu-id="88ec7-131">在目前的方法內定義一組序列點。</span><span class="sxs-lookup"><span data-stu-id="88ec7-131">Defines a group of sequence points within the current method.</span></span>|  
|[<span data-ttu-id="88ec7-132">GetDebugInfo 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-132">GetDebugInfo Method</span></span>](isymunmanagedwriter-getdebuginfo-method.md)|<span data-ttu-id="88ec7-133">傳回編譯器在可移植執行檔（PE）檔案標頭中寫入 debug 目錄專案所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="88ec7-133">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span>|  
|[<span data-ttu-id="88ec7-134">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-134">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)|<span data-ttu-id="88ec7-135">設定此寫入器將與之關聯的中繼資料發射器介面，並設定要寫入偵錯工具符號的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="88ec7-135">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>|  
|[<span data-ttu-id="88ec7-136">Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-136">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)|<span data-ttu-id="88ec7-137">設定與此寫入器相關聯的中繼資料發射器介面，設定要寫入偵錯工具符號的輸出檔案名，並設定程式資料庫（PDB）檔案的最終位置。</span><span class="sxs-lookup"><span data-stu-id="88ec7-137">Sets the metadata emitter interface with which this writer will be associated, sets the output file name to which the debugging symbols will be written, and sets the final location of the program database (PDB) file.</span></span>|  
|[<span data-ttu-id="88ec7-138">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-138">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)|<span data-ttu-id="88ec7-139">開啟用來發出符號資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="88ec7-139">Opens a method into which symbol information is emitted.</span></span>|  
|[<span data-ttu-id="88ec7-140">OpenNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-140">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)|<span data-ttu-id="88ec7-141">開啟新的命名空間。</span><span class="sxs-lookup"><span data-stu-id="88ec7-141">Opens a new namespace.</span></span>|  
|[<span data-ttu-id="88ec7-142">OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-142">OpenScope Method</span></span>](isymunmanagedwriter-openscope-method.md)|<span data-ttu-id="88ec7-143">開啟目前方法中的新語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="88ec7-143">Opens a new lexical scope in the current method.</span></span>|  
|[<span data-ttu-id="88ec7-144">RemapToken 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-144">RemapToken Method</span></span>](isymunmanagedwriter-remaptoken-method.md)|<span data-ttu-id="88ec7-145">通知符號寫入器，元資料標記在發出中繼資料時已重新對應。</span><span class="sxs-lookup"><span data-stu-id="88ec7-145">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span>|  
|[<span data-ttu-id="88ec7-146">SetMethodSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-146">SetMethodSourceRange Method</span></span>](isymunmanagedwriter-setmethodsourcerange-method.md)|<span data-ttu-id="88ec7-147">指定原始程式檔內方法的實際開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="88ec7-147">Specifies the true start and end of a method within a source file.</span></span>|  
|[<span data-ttu-id="88ec7-148">SetScopeRange 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-148">SetScopeRange Method</span></span>](isymunmanagedwriter-setscoperange-method.md)|<span data-ttu-id="88ec7-149">定義指定語彙範圍的位移範圍。</span><span class="sxs-lookup"><span data-stu-id="88ec7-149">Defines the offset range for the specified lexical scope.</span></span>|  
|[<span data-ttu-id="88ec7-150">SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-150">SetSymAttribute Method</span></span>](isymunmanagedwriter-setsymattribute-method.md)|<span data-ttu-id="88ec7-151">根據名稱定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="88ec7-151">Defines a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="88ec7-152">SetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-152">SetUserEntryPoint Method</span></span>](isymunmanagedwriter-setuserentrypoint-method.md)|<span data-ttu-id="88ec7-153">指定使用者定義的方法，這是此模組的進入點。</span><span class="sxs-lookup"><span data-stu-id="88ec7-153">Specifies the user-defined method that is the entry point for this module.</span></span>|  
|[<span data-ttu-id="88ec7-154">UsingNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="88ec7-154">UsingNamespace Method</span></span>](isymunmanagedwriter-usingnamespace-method.md)|<span data-ttu-id="88ec7-155">指定在目前開啟的詞法範圍內使用指定的完整命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="88ec7-155">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88ec7-156">需求</span><span class="sxs-lookup"><span data-stu-id="88ec7-156">Requirements</span></span>  
 <span data-ttu-id="88ec7-157">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="88ec7-157">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ec7-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88ec7-158">See also</span></span>

- [<span data-ttu-id="88ec7-159">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="88ec7-159">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="88ec7-160">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="88ec7-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="88ec7-161">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="88ec7-161">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
