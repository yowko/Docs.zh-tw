---
title: "&lt;例外狀況&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="0e4ba-102">&lt;例外狀況&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e4ba-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="0e4ba-103">指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e4ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e4ba-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e4ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e4ba-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="0e4ba-106">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="0e4ba-107">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="0e4ba-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="0e4ba-109">描述。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e4ba-110">備註</span><span class="sxs-lookup"><span data-stu-id="0e4ba-110">Remarks</span></span>  
 <span data-ttu-id="0e4ba-111">使用`<exception>`標記來指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="0e4ba-112">此標記會套用到方法定義。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="0e4ba-113">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e4ba-114">範例</span><span class="sxs-lookup"><span data-stu-id="0e4ba-114">Example</span></span>  
 <span data-ttu-id="0e4ba-115">這個範例會使用`<exception>`標記來描述例外狀況，`IntDivide`函式可能擲回。</span><span class="sxs-lookup"><span data-stu-id="0e4ba-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0e4ba-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e4ba-116">See Also</span></span>  
 [<span data-ttu-id="0e4ba-117">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="0e4ba-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
