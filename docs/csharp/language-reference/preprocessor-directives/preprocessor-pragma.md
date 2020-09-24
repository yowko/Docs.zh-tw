---
description: '#pragma - C# 參考'
title: '#pragma - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 2788c2589bee149676c5cb2b4212ec7a060a47af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168513"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="746dd-103">#pragma (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="746dd-103">#pragma (C# Reference)</span></span>

<span data-ttu-id="746dd-104">`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。</span><span class="sxs-lookup"><span data-stu-id="746dd-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="746dd-105">編譯器必須支援指示。</span><span class="sxs-lookup"><span data-stu-id="746dd-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="746dd-106">換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。</span><span class="sxs-lookup"><span data-stu-id="746dd-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="746dd-107">Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：</span><span class="sxs-lookup"><span data-stu-id="746dd-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="746dd-108">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="746dd-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="746dd-109">#pragma 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="746dd-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="746dd-110">語法</span><span class="sxs-lookup"><span data-stu-id="746dd-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="746dd-111">參數</span><span class="sxs-lookup"><span data-stu-id="746dd-111">Parameters</span></span>  

 `pragma-name`  
 <span data-ttu-id="746dd-112">可辨識的 pragma 名稱。</span><span class="sxs-lookup"><span data-stu-id="746dd-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="746dd-113">Pragma 特定引數。</span><span class="sxs-lookup"><span data-stu-id="746dd-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746dd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="746dd-114">See also</span></span>

- [<span data-ttu-id="746dd-115">C # 參考</span><span class="sxs-lookup"><span data-stu-id="746dd-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="746dd-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="746dd-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="746dd-117">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="746dd-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="746dd-118">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="746dd-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="746dd-119">#pragma 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="746dd-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
