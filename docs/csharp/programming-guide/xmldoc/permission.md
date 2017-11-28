---
title: "&lt;permission&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37bb37ea14edc1f91225f9b04b18b354d99579b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="bc68a-102">&lt;permission&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bc68a-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="bc68a-103">語法</span><span class="sxs-lookup"><span data-stu-id="bc68a-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc68a-104">參數</span><span class="sxs-lookup"><span data-stu-id="bc68a-104">Parameters</span></span>  
 <span data-ttu-id="bc68a-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="bc68a-105">cref = " `member`"</span></span>  
 <span data-ttu-id="bc68a-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="bc68a-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="bc68a-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="bc68a-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="bc68a-108">member 必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="bc68a-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="bc68a-109">如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](../../../csharp/programming-guide/xmldoc/see.md)。</span><span class="sxs-lookup"><span data-stu-id="bc68a-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="bc68a-110">成員存取權的描述。</span><span class="sxs-lookup"><span data-stu-id="bc68a-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc68a-111">備註</span><span class="sxs-lookup"><span data-stu-id="bc68a-111">Remarks</span></span>  
 <span data-ttu-id="bc68a-112">\<permission> 標記可讓您記載成員存取權。</span><span class="sxs-lookup"><span data-stu-id="bc68a-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="bc68a-113"><xref:System.Security.PermissionSet> 類別可讓您指定成員存取權。</span><span class="sxs-lookup"><span data-stu-id="bc68a-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="bc68a-114">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="bc68a-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc68a-115">範例</span><span class="sxs-lookup"><span data-stu-id="bc68a-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bc68a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc68a-116">See Also</span></span>  
 [<span data-ttu-id="bc68a-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bc68a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bc68a-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="bc68a-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
