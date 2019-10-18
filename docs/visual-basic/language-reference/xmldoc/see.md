---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e3ae5fb63540e47e5b8da2e2d60d5bd736e019d7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524653"
---
# <a name="see-visual-basic"></a><span data-ttu-id="127ce-102">\<see > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="127ce-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="127ce-103">指定另一個成員的連結。</span><span class="sxs-lookup"><span data-stu-id="127ce-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="127ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="127ce-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="127ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="127ce-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="127ce-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="127ce-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="127ce-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="127ce-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="127ce-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="127ce-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="127ce-109">備註</span><span class="sxs-lookup"><span data-stu-id="127ce-109">Remarks</span></span>  
 <span data-ttu-id="127ce-110">使用 `<see>` 標籤，指定文字內的連結。</span><span class="sxs-lookup"><span data-stu-id="127ce-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="127ce-111">使用[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md)來表示您可能想要出現在「另請參閱」一節中的文字。</span><span class="sxs-lookup"><span data-stu-id="127ce-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="127ce-112">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="127ce-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="127ce-113">範例</span><span class="sxs-lookup"><span data-stu-id="127ce-113">Example</span></span>  
 <span data-ttu-id="127ce-114">這個範例會使用 `UpdateRecord` 備註區段中的 `<see>` 標記來參考 `DoesRecordExist` 方法。</span><span class="sxs-lookup"><span data-stu-id="127ce-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="127ce-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="127ce-115">See also</span></span>

- [<span data-ttu-id="127ce-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="127ce-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
