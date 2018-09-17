---
title: '&lt;例外狀況&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 047805ad91d87550da80448fd10883ae58647bd6
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687409"
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="6d790-102">&lt;例外狀況&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d790-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="6d790-103">指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d790-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d790-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d790-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d790-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d790-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="6d790-106">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="6d790-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="6d790-107">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="6d790-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="6d790-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="6d790-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6d790-109">描述。</span><span class="sxs-lookup"><span data-stu-id="6d790-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d790-110">備註</span><span class="sxs-lookup"><span data-stu-id="6d790-110">Remarks</span></span>  
 <span data-ttu-id="6d790-111">使用`<exception>`標記來指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6d790-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="6d790-112">此標記會套用到方法定義。</span><span class="sxs-lookup"><span data-stu-id="6d790-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="6d790-113">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="6d790-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d790-114">範例</span><span class="sxs-lookup"><span data-stu-id="6d790-114">Example</span></span>  
 <span data-ttu-id="6d790-115">這個範例會使用`<exception>`標記來描述例外狀況，`IntDivide`函式可能會擲回。</span><span class="sxs-lookup"><span data-stu-id="6d790-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d790-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d790-116">See Also</span></span>  
 [<span data-ttu-id="6d790-117">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="6d790-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
