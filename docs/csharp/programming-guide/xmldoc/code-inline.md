---
title: '&lt;c&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: b789b95c5e23534fb36613ac9203f146b265a98d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640975"
---
# <a name="ltcgt-c-programming-guide"></a><span data-ttu-id="ab495-102">&lt;c&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ab495-102">&lt;c&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ab495-103">語法</span><span class="sxs-lookup"><span data-stu-id="ab495-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab495-104">參數</span><span class="sxs-lookup"><span data-stu-id="ab495-104">Parameters</span></span>  
 `text`  
 <span data-ttu-id="ab495-105">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="ab495-105">The text you would like to indicate as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab495-106">備註</span><span class="sxs-lookup"><span data-stu-id="ab495-106">Remarks</span></span>  
 <span data-ttu-id="ab495-107">\<c> 標記可讓您在一段描述中指出應該標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="ab495-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="ab495-108">請使用 [\<code>](../../../csharp/programming-guide/xmldoc/code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab495-108">Use [\<code>](../../../csharp/programming-guide/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="ab495-109">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="ab495-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab495-110">範例</span><span class="sxs-lookup"><span data-stu-id="ab495-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ab495-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab495-111">See also</span></span>

- [<span data-ttu-id="ab495-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ab495-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ab495-113">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="ab495-113">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
