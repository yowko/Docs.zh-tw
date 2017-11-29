---
title: "&lt;請參閱&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 010a3403d7748653648b323ad07f52bf93db2879
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="d4812-102">&lt;請參閱&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4812-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="d4812-103">指定另一個成員的連結。</span><span class="sxs-lookup"><span data-stu-id="d4812-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4812-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4812-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4812-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4812-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="d4812-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="d4812-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d4812-107">編譯器會檢查指定的程式碼項目存在，而且傳遞`member`在輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="d4812-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="d4812-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="d4812-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4812-109">備註</span><span class="sxs-lookup"><span data-stu-id="d4812-109">Remarks</span></span>  
 <span data-ttu-id="d4812-110">使用`<see>`標記加入至指定文字中的連結。</span><span class="sxs-lookup"><span data-stu-id="d4812-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="d4812-111">使用[ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md)表示您可能想要出現在 「 另請參閱 」 一節中的文字。</span><span class="sxs-lookup"><span data-stu-id="d4812-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="d4812-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="d4812-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4812-113">範例</span><span class="sxs-lookup"><span data-stu-id="d4812-113">Example</span></span>  
 <span data-ttu-id="d4812-114">這個範例會使用`<see>`標記`UpdateRecord`< 備註 > 一節，來參考`DoesRecordExist`方法。</span><span class="sxs-lookup"><span data-stu-id="d4812-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d4812-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4812-115">See Also</span></span>  
 [<span data-ttu-id="d4812-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="d4812-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
