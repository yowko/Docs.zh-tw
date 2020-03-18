---
title: '#pragma - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712451"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="cc133-102">#pragma (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cc133-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="cc133-103">`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。</span><span class="sxs-lookup"><span data-stu-id="cc133-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="cc133-104">編譯器必須支援指示。</span><span class="sxs-lookup"><span data-stu-id="cc133-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="cc133-105">換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。</span><span class="sxs-lookup"><span data-stu-id="cc133-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="cc133-106">Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：</span><span class="sxs-lookup"><span data-stu-id="cc133-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="cc133-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="cc133-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="cc133-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="cc133-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="cc133-109">語法</span><span class="sxs-lookup"><span data-stu-id="cc133-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc133-110">參數</span><span class="sxs-lookup"><span data-stu-id="cc133-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="cc133-111">可辨識的 pragma 名稱。</span><span class="sxs-lookup"><span data-stu-id="cc133-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="cc133-112">Pragma 特定引數。</span><span class="sxs-lookup"><span data-stu-id="cc133-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc133-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc133-113">See also</span></span>

- [<span data-ttu-id="cc133-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cc133-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cc133-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cc133-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cc133-116">C# 預處理器指令</span><span class="sxs-lookup"><span data-stu-id="cc133-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="cc133-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="cc133-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="cc133-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="cc133-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
