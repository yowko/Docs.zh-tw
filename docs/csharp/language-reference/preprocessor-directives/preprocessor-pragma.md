---
title: "#<a name=\"pragma-c-reference\"></a>pragma (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma'
helpviewer_keywords: '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a><span data-ttu-id="a0f08-102">#pragma (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a0f08-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="a0f08-103">`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。</span><span class="sxs-lookup"><span data-stu-id="a0f08-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="a0f08-104">編譯器必須支援指示。</span><span class="sxs-lookup"><span data-stu-id="a0f08-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="a0f08-105">換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。</span><span class="sxs-lookup"><span data-stu-id="a0f08-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="a0f08-106">Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：</span><span class="sxs-lookup"><span data-stu-id="a0f08-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="a0f08-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="a0f08-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="a0f08-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="a0f08-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="a0f08-109">語法</span><span class="sxs-lookup"><span data-stu-id="a0f08-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0f08-110">參數</span><span class="sxs-lookup"><span data-stu-id="a0f08-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="a0f08-111">可辨識的 pragma 名稱。</span><span class="sxs-lookup"><span data-stu-id="a0f08-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="a0f08-112">Pragma 特定引數。</span><span class="sxs-lookup"><span data-stu-id="a0f08-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f08-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0f08-113">See Also</span></span>  
 [<span data-ttu-id="a0f08-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a0f08-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a0f08-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a0f08-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a0f08-116">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="a0f08-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="a0f08-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="a0f08-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="a0f08-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="a0f08-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
