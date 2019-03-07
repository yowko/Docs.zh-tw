---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: c26e818276eb4654fec77230372a0ae090952961
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474835"
---
# <a name="see-visual-basic"></a><span data-ttu-id="12624-102">\<請參閱 > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12624-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="12624-103">指定另一個成員的連結。</span><span class="sxs-lookup"><span data-stu-id="12624-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12624-104">語法</span><span class="sxs-lookup"><span data-stu-id="12624-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="12624-105">參數</span><span class="sxs-lookup"><span data-stu-id="12624-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="12624-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="12624-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="12624-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="12624-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="12624-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="12624-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12624-109">備註</span><span class="sxs-lookup"><span data-stu-id="12624-109">Remarks</span></span>  
 <span data-ttu-id="12624-110">使用`<see>`標記即可指定文字中的連結。</span><span class="sxs-lookup"><span data-stu-id="12624-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="12624-111">使用[ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md)指出要顯示 「 請參閱 < 另請參閱 > 一節中的文字。</span><span class="sxs-lookup"><span data-stu-id="12624-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="12624-112">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="12624-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12624-113">範例</span><span class="sxs-lookup"><span data-stu-id="12624-113">Example</span></span>  
 <span data-ttu-id="12624-114">這個範例會使用`<see>`標記中的`UpdateRecord`註解區段來參考`DoesRecordExist`方法。</span><span class="sxs-lookup"><span data-stu-id="12624-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="12624-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12624-115">See also</span></span>
- [<span data-ttu-id="12624-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="12624-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
