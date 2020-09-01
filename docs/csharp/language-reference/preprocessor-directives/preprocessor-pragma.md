---
description: '#pragma - C# 參考'
title: '#pragma - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137951"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="7955f-103">#pragma (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7955f-103">#pragma (C# Reference)</span></span>
<span data-ttu-id="7955f-104">`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。</span><span class="sxs-lookup"><span data-stu-id="7955f-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="7955f-105">編譯器必須支援指示。</span><span class="sxs-lookup"><span data-stu-id="7955f-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="7955f-106">換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。</span><span class="sxs-lookup"><span data-stu-id="7955f-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="7955f-107">Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：</span><span class="sxs-lookup"><span data-stu-id="7955f-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="7955f-108">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="7955f-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="7955f-109">#pragma 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="7955f-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="7955f-110">語法</span><span class="sxs-lookup"><span data-stu-id="7955f-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="7955f-111">參數</span><span class="sxs-lookup"><span data-stu-id="7955f-111">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="7955f-112">可辨識的 pragma 名稱。</span><span class="sxs-lookup"><span data-stu-id="7955f-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="7955f-113">Pragma 特定引數。</span><span class="sxs-lookup"><span data-stu-id="7955f-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7955f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7955f-114">See also</span></span>

- [<span data-ttu-id="7955f-115">C # 參考</span><span class="sxs-lookup"><span data-stu-id="7955f-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7955f-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7955f-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7955f-117">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="7955f-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="7955f-118">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="7955f-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="7955f-119">#pragma 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="7955f-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
