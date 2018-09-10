---
title: '#pragma (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 5ae397cc61e0c6b58ed2079369131ebb7e352eae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43747479"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="99766-102">#pragma (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="99766-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="99766-103">`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。</span><span class="sxs-lookup"><span data-stu-id="99766-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="99766-104">編譯器必須支援指示。</span><span class="sxs-lookup"><span data-stu-id="99766-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="99766-105">換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。</span><span class="sxs-lookup"><span data-stu-id="99766-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="99766-106">Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：</span><span class="sxs-lookup"><span data-stu-id="99766-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="99766-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="99766-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="99766-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="99766-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="99766-109">語法</span><span class="sxs-lookup"><span data-stu-id="99766-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99766-110">參數</span><span class="sxs-lookup"><span data-stu-id="99766-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="99766-111">可辨識的 pragma 名稱。</span><span class="sxs-lookup"><span data-stu-id="99766-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="99766-112">Pragma 特定引數。</span><span class="sxs-lookup"><span data-stu-id="99766-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99766-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="99766-113">See Also</span></span>

- [<span data-ttu-id="99766-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="99766-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="99766-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="99766-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="99766-116">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="99766-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="99766-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="99766-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [<span data-ttu-id="99766-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="99766-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
