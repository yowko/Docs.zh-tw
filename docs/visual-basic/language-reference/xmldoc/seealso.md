---
title: '&lt;seealso&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: a792bbea108bcdf33d430c47773466ef3dccdb0c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171864"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="1d8dc-102">&lt;seealso&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d8dc-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="1d8dc-103">指定另請參閱 > 一節中所顯示的連結。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d8dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d8dc-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d8dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d8dc-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="1d8dc-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1d8dc-107">編譯器會檢查指定的程式碼項目存在，並將傳遞`member`輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="1d8dc-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d8dc-109">備註</span><span class="sxs-lookup"><span data-stu-id="1d8dc-109">Remarks</span></span>  
 <span data-ttu-id="1d8dc-110">使用`<seealso>`標記即可指定您想要另請參閱 > 一節中所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="1d8dc-111">使用 [\<see>](../../../visual-basic/language-reference/xmldoc/see.md)，以在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="1d8dc-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d8dc-113">範例</span><span class="sxs-lookup"><span data-stu-id="1d8dc-113">Example</span></span>  
 <span data-ttu-id="1d8dc-114">這個範例會使用`<seealso>`標記中的`DoesRecordExist`註解區段來參考`UpdateRecord`方法。</span><span class="sxs-lookup"><span data-stu-id="1d8dc-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d8dc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d8dc-115">See Also</span></span>  
 [<span data-ttu-id="1d8dc-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="1d8dc-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
