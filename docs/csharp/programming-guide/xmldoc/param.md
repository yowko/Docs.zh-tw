---
title: "&lt;param&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a5325b91130623442c9cf5453e52418bb44cc34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="9bd44-102">&lt;param&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9bd44-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9bd44-103">語法</span><span class="sxs-lookup"><span data-stu-id="9bd44-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bd44-104">參數</span><span class="sxs-lookup"><span data-stu-id="9bd44-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9bd44-105">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bd44-105">The name of a method parameter.</span></span> <span data-ttu-id="9bd44-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="9bd44-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9bd44-107">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="9bd44-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bd44-108">備註</span><span class="sxs-lookup"><span data-stu-id="9bd44-108">Remarks</span></span>  
 <span data-ttu-id="9bd44-109">\<param> 標記應該在方法宣告的註解中用來描述參數的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="9bd44-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="9bd44-110">若要記錄多個參數，請使用多個 \<param > 標記。</span><span class="sxs-lookup"><span data-stu-id="9bd44-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="9bd44-111">\<param> 標記的文字將會顯示於 IntelliSense (即物件瀏覽器) 以及程式碼結構 Web 報告中。</span><span class="sxs-lookup"><span data-stu-id="9bd44-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="9bd44-112">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="9bd44-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd44-113">範例</span><span class="sxs-lookup"><span data-stu-id="9bd44-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9bd44-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bd44-114">See Also</span></span>  
 [<span data-ttu-id="9bd44-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9bd44-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9bd44-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="9bd44-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
